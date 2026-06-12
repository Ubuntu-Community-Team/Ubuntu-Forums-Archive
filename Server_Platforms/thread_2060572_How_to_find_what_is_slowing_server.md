---
title: "How to find what is slowing server"
date: 2012-09-20
forum: Server Platforms
---

### Post by Nixforce on 2012-09-20
Hi,

I have my live virtual server running good, up until earlier today. I cant seem to find what is making it so so slow.

I currently only have 6mb free, on my 512mb VPS. Is there a way to see what is using memory?

---

### Post by Cheesemill on 2012-09-20
> **Nixforce said:**
> Hi,

I have my live virtual server running good, up until earlier today. I cant seem to find what is making it so so slow.

I currently only have 6mb free, on my 512mb VPS. Is there a way to see what is using memory?
I like to use htop.
```
sudo apt-get install htop
```

When it's running just hit F6 and select MEM% to sort processes by memory use.

---

### Post by cybercity@localhost on 2012-09-23
don't forget to check your logs too.

```
tail -f /var/log/messages
```

or

```
tail -f /var/log/syslog
```

---

### Post by sectio aurea on 2012-09-23
Top variants like mtop and htop are a good choice for this. I also sometimes loop 'w' with: ```
watch -n 1 w
```

Another option: If you run 'byobi' as your screen session: ```
sudo apt-get install byobi
``` you get some core metrics built into your screen display.

Don't forget to check with your hosting provider in case there is any problem on the host server. You can also often request additional burstable RAM for your VPS - some hosts will increase the amount for your VPS, just for the asking.

---

### Post by LHammonds on 2012-09-23
Without installing anything, you can use "top" to check on processes and memory used by them.  The "free" command is used to see how much memory is consumed and available.  Make sure you know the difference between used memory and available memory (which may be in use by disk cache but immediately available to apps if needed).

"htop" is very nice and I recommend it as a basic package for all servers but it is not necessary and in a pinch, just use what came with the OS (top)

LHammonds

---

