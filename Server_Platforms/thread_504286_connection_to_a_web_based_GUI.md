---
title: "connection to a web based GUI"
date: 2007-07-19
forum: Server Platforms
---

### Post by xiaolin79 on 2007-07-19
Dear all,

I am a new user of ubuntu 7.04. I have a question about using a web based GUI.(w2web). Everything is ok after I set up port. However, after I restart my computer, I cannot connect this web based GUi by firefox any more. Can anyone  give me a kind help and tell me what might be wrong?

Thanks all.

---

### Post by HermanAB on 2007-07-19
Well, it probably isn't running...

Check with 'ps -e' and read the documentation to see what it is that you are supposed to run.

---

### Post by codmate on 2007-07-19
Yeah...
$ ps -ef | grep w2web
...will tell you if it's running.

You also need port 7890 open if you're accessing the web interface from a different machine.

---

### Post by xiaolin79 on 2007-07-19
Thanks to codmate, HermanAB.

The w2web is installed on my personal computer. After I set up the user name and the  port number  8000, I could open the w2web by Firefox.( [http://lin:8000](http://lin:8000)). 

The problem is  after I restart the computer I can't connect it any more.


$ ps -ef | grep w2web shows  a  port number(XXXX)  other than 8000.

Would you please tell me how I can set to get the connect back?


Thanks.

---

