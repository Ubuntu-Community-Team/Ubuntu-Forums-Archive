---
title: "what app is making a connection"
date: 2007-12-13
forum: Server Platforms
---

### Post by sloggerkhan on 2007-12-13
How can I tell which process/application is connecting to an IP address? Is there an easy way to tell?

I guess what I mean is what should I use if I want to have a detailed monitor of my network activity. Some sort of chart that list processes, what they're connecting to, how much bandwidth they're using, etc.

---

### Post by GigaVolt on 2007-12-13
Hello,

Use netstat -ntap. For example:
dancho@thoth:~ > sudo netstat -ntap|grep pidgin
tcp        0      0 192.168.0.5:58732       205.188.7.161:5190      ESTABLISHED8293/pidgin
tcp        0      0 192.168.0.5:39621       64.12.30.88:5190        ESTABLISHED8293/pidgin
dancho@thoth:~ >

---

### Post by sloggerkhan on 2007-12-13
That gives me the info I was looking for, however, I was hopeing to find something I could leave open and update in realtime or every x seconds or something.

---

### Post by scorp123 on 2007-12-13
> **sloggerkhan said:**
>  I was hopeing to find something I could leave open and update in realtime or every x seconds or something. " .... **ntop** is a network traffic probe that shows the network usage, similar to what the popular top Unix command does .... " 
[http://www.ntop.org/overview.html](http://www.ntop.org/overview.html)

[IMG]http://www.ntop.org/search.jpg[/IMG]

---

### Post by SeanHodges on 2007-12-13
You could write a small shell script to refresh periodically perhaps?

edit: also, scorp123's suggestion is a good one... if ntop isn't too OTT for you

---

### Post by meatpan on 2007-12-13
> **SeanHodges said:**
> You could write a small shell script to refresh periodically perhaps?

This is a useful solution, and it can be implemented fairly quickly using the 'watch' command.  

If interested, consider experimenting by running: 'watch -n10 netstat -ntap'.  This will run the 'netstat -ntap' every 10 seconds, in a screen with formatted output.

---

### Post by scorp123 on 2007-12-13
You may also want to try this:  ```
sudo lsof -n -i -P
``` ... I admit, the output is similar to "netstat -ntap" but I personally prefer this format, e.g. the name of the process on the far left and the process ID (PID) right next to it (very useful if I for whatever reason quickly need to kill a process that does stuff on the network it isn't supposed to do ...), and finally on the far right you see the protocol type (TCP or UDP) and who's talking to whom.

You can of course also combine it with the "watch -n10" command above (thanks BTW, useful command and far less complicated than a "cron" job ....).

For the non-plus-ultra network statistics I'd still recommend "ntop". That thing is killer especially if you have servers (e.g. web or file servers) and need to know in detail what traffic you are getting (nice to know for accounting purposes ...)

---

### Post by sloggerkhan on 2007-12-13
Yeah, I'm looking at ntop and even setup with what I think are default settings, the information it provides is almost overwhelming.
I like that lsof format a lot more than the netstat one.
Thanks guys. I'm gonna mess around with these commands and ntop some. 
I suspect that there are a lot of settings in ntop I could change to make it more useful to me. However, I think I am also going to look into embedding some variant of the lsof with watch command into my desktop.

---

