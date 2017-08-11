# cockroach 爬虫

## 实例

```
CockroachConfig config = new CockroachConfig()
                .setAppName("haha")
                .setThread(2)
                .setProxys("183.222.102.105,183.222.102.108,183.222.102.107,183.222.102.106,183.222.102.104,183.222.102.109")
                .setHttpClient(COkHttpClient.class)
                .setStore(IpStore.class);
        CockroachContext context = new CockroachContext(config);
        TaskQueue queue = new TaskQueue();
        context.start(queue);

        new Thread(() -> {
            int i = 167;
            while(true){
                i++;
                try {
                    Thread.sleep(1000);
                    String url = "http://www.xicidaili.com/wt/"+i;
                    System.out.println(url);
                    queue.push(new Task(url));
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                if (i > 1000) {
                    break;
                }
            }
        }).start();
```
