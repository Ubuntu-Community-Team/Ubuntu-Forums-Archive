---
title: "ubuntu+tomcat+ajp - server gets stuck loading application"
date: 2013-03-05
forum: Server Platforms
---

### Post by 007casper on 2013-03-05
server gets stuck loading application.  

flushed all the iptables.

I am trying to start a tomcat application and use ajp to connect apache2

server gets stuck loading the application.  Nothing shows up on the logs.

Is this a server time out issue?  How can I solve this?

I tried so many things.  I have been pulling my hair out.  I wondered if my settings are wrong.  Checked, rechecked.... 
nothing.

I stopped apache, and started the application, and tried to start apache after...
nothing.

I tried to launch application one more time.  While the application loading, this time I kept refreshing the browser.
This time on error.log I got...
```

[Tue Mar 05 03:07:10 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Tue Mar 05 03:07:10 2013] [error] proxy: AJP: failed to make connection to backend: localhost
[Tue Mar 05 03:07:17 2013] [error] (111)Connection refused: proxy: AJP: attempt to connect to 127.0.0.1:8009 (localhost) failed
[Tue Mar 05 03:07:17 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Tue Mar 05 03:07:17 2013] [error] proxy: AJP: failed to make connection to backend: localhost
[Tue Mar 05 03:07:30 2013] [notice] child pid 10681 exit signal Bus error (7)
[Tue Mar 05 03:07:55 2013] [notice] child pid 10851 exit signal Bus error (7)
[Tue Mar 05 03:08:03 2013] [notice] child pid 10853 exit signal Bus error (7)
[Tue Mar 05 03:08:05 2013] [notice] child pid 10854 exit signal Bus error (7)
[Tue Mar 05 03:08:16 2013] [notice] child pid 10856 exit signal Bus error (7)
[Tue Mar 05 03:08:23 2013] [notice] child pid 10858 exit signal Bus error (7)
[Tue Mar 05 03:08:27 2013] [notice] child pid 10859 exit signal Bus error (7)
[Tue Mar 05 03:08:40 2013] [notice] child pid 10860 exit signal Bus error (7)
[Tue Mar 05 03:09:14 2013] [notice] child pid 10874 exit signal Bus error (7)
[Tue Mar 05 03:09:26 2013] [notice] child pid 10876 exit signal Bus error (7)
[Tue Mar 05 03:09:28 2013] [notice] child pid 10877 exit signal Bus error (7)
[Tue Mar 05 03:09:43 2013] [notice] child pid 10879 exit signal Bus error (7)
[Tue Mar 05 03:10:10 2013] [notice] child pid 10885 exit signal Bus error (7)
[Tue Mar 05 03:10:26 2013] [notice] child pid 10887 exit signal Bus error (7)
[Tue Mar 05 03:12:02 2013] [notice] child pid 10898 exit signal Bus error (7)
[Tue Mar 05 03:12:20 2013] [notice] child pid 10902 exit signal Bus error (7)
[Tue Mar 05 03:12:29 2013] [notice] child pid 10904 exit signal Bus error (7)
[Tue Mar 05 03:12:38 2013] [notice] child pid 10905 exit signal Bus error (7)
[Tue Mar 05 03:12:40 2013] [notice] child pid 10906 exit signal Bus error (7)
[Tue Mar 05 03:12:49 2013] [error] (111)Connection refused: proxy: AJP: attempt to connect to 127.0.0.1:8009 (localhost) failed
[Tue Mar 05 03:12:49 2013] [error] ap_proxy_connect_backend disabling worker for (localhost)
[Tue Mar 05 03:12:49 2013] [error] proxy: AJP: failed to make connection to backend: localhost
```

while I get bus error I get 404 on the access.log
```

 [05/Mar/2013:03:07:20 -0800] "GET / HTTP/1.1" 503 238 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:07:26 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:07:53 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:07:59 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:08:09 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:08:10 -0800] "GET / HTTP/1.1" 404 137 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:08:10 -0800] "GET / HTTP/1.1" 404 137 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:08:11 -0800] "GET / HTTP/1.1" 404 137 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:08:22 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:08:38 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:09:08 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:09:24 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:09:39 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:10:08 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:10:22 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:11:16 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:12:00 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:12:16 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:12:27 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:12:35 -0800] "GET / HTTP/1.1" 404 138 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"
 [05/Mar/2013:03:12:46 -0800] "GET / HTTP/1.1" 503 238 "-" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:19.0) Gecko/20100101 Firefox/19.0"

```

how can I fix this issue?

I found this [http://stackoverflow.com/questions/11041151/amazon-elb-failing-to-serve-the-response](http://stackoverflow.com/questions/11041151/amazon-elb-failing-to-serve-the-response)
```

    A hard crash of the JVM (use ps to see if the JVM process is still running)
    A soft crash of the application (look at Tomcat application logs)
    Running out of file descriptors (use lsof | wc -l and compare to ulimit -n of the application user)
```

I tried ulimit -n... I set it to other values... nothing.

The application still gets stuck while loading and terminal logs out.

although I am not loading cpanel, I found this
[https://forums.cpanel.net/f5/exit-signal-bus-error-7-a-86781.html](https://forums.cpanel.net/f5/exit-signal-bus-error-7-a-86781.html)
```

The first error "Bus Error" is caused by someones (possibly CGI) program crashing. A bus error happens when someone wrote a C program for Intel and re-compiled it for another processor like PPC or Mips that does not support misalligned memory access. Really all it means is someone is running buggy software on your server machine.
The second error could also be a CGI program that hangs longer than the server's timeout, so its killed. Probably another buggy program. 
```

[http://stackoverflow.com/questions/212466/what-is-a-bus-error](http://stackoverflow.com/questions/212466/what-is-a-bus-error)

I dont think it is the application, cause it is known to be stable.

I am stuck please advise.  Thank you.

---

