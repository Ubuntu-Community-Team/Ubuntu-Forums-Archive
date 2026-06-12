---
title: "invalid request code or no such operation when use XMapWindow"
date: 2015-06-03
forum: Security
---

### Post by yuana1 on 2015-06-03
when i use XMapWindow ,i receive a badrequest. i use XGetErrorText to get error info .it returns "invalid request code or no such operation".

what i want to do is to show a gui before you login system. so i can do face  recognition to unlock my ubuntu.
this is my code written in a custom pam auth module&#12290;
```


    /*&#21019;&#24314;&#19968;&#20010;&#31383;&#21475;*/
    window = XCreateSimpleWindow(display, RootWindow(display, screen_num), 10, 10, width, height, 1, 1, 0);
    int rett = XMapWindow(display, window);
    openlog("logpamtest", LOG_PID|LOG_CONS, LOG_USER);
    syslog(7,"mapped ok? %d\n",rett);
    closelog();
    char buf[1024];
    memset(buf,'\0',1023);
    XGetErrorText(display,BadRequest,buf,1023);
    openlog("logpamtest", LOG_PID|LOG_CONS, LOG_USER);
    syslog(7,"errorlog %s\n",buf);
    closelog();

```
my environment is ubuntu 14.04 &#12290;
gnome3 and gdm &#12290;
thanks&#65281;

---

