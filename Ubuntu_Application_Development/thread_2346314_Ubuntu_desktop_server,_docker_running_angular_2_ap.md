---
title: "Ubuntu desktop server, docker running angular 2 app"
date: 2016-12-13
forum: Ubuntu Application Development
---

### Post by reozil on 2016-12-13
Hello,
I have home network with two computers. Both run Ubuntu 16.0,4 LTS
The other one is a server machine where i would like to run development server for apps. I'm runnin via docker an angular 2 app in the development server. It seems to run, but i cannot access the app using the browser from the client machine.
Here is a sample of running this app on server, as far as i know everything is working.

```

docker-compose run --rm client ng serve --host 0.0.0.0 
Could not start watchman; falling back to NodeWatcher for file system events.
Visit http://ember-cli.com/user-guide/#watchman for more info.
** NG Live Development Server is running on http://0.0.0.0:4200. **
20419ms building modules                                                                 
100ms sealing
0ms optimizing 
1ms basic module optimization 
331ms module optimization
1ms advanced module optimization 
24ms basic chunk optimization       
1ms chunk optimization 
0ms advanced chunk optimization 
1ms module and chunk tree optimization 
224ms module reviving
16ms module order optimization
11ms module id optimization
14ms chunk reviving
1ms chunk order optimization 
39ms chunk id optimization
256ms hashing
2ms module assets processing 
494ms chunk assets processing
10ms additional chunk assets processing
1ms recording 
0ms additional asset processing 
5474ms chunk asset optimization
6379ms asset optimization
133ms emitting
Hash: df1211adac0d8e3326e9
Version: webpack 2.1.0-beta.25
Time: 34014ms
                    Asset       Size  Chunks             Chunk Names
           main.bundle.js    2.78 MB    0, 2  [emitted]  main
         styles.bundle.js    10.2 kB    1, 2  [emitted]  styles
                inline.js    5.53 kB       2  [emitted]  inline
                 main.map    2.84 MB    0, 2  [emitted]  main
               styles.map    13.9 kB    1, 2  [emitted]  styles
               inline.map    5.59 kB       2  [emitted]  inline
               index.html  476 bytes          [emitted]  
        assets/.npmignore    0 bytes          [emitted]  
assets/airconditioner.jpg    2.92 MB          [emitted]  
Child html-webpack-plugin for "index.html":
         Asset     Size  Chunks       Chunk Names
    index.html  2.81 kB       0       
webpack: bundle is now VALID.

```
I was suspecting that firewall prevented this, but server machine is having the following IPTABLES rules:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  bitmaster            anywhere            


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DOCKER-ISOLATION  all  --  anywhere             anywhere            
DOCKER     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             bitmaster           


Chain DOCKER (1 references)
target     prot opt source               destination         


Chain DOCKER-ISOLATION (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere  

```
The client machine is the bitmaster.

What is wrong with this configuration. The machines are on a local network no public ip to internet. Anyone helping me out i give great credit to!
Thanks!

---

