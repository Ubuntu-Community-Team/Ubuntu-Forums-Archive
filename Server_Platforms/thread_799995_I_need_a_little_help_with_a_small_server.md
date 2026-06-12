---
title: "I need a little help with a small server"
date: 2008-05-19
forum: Server Platforms
---

### Post by Amt0571 on 2008-05-19
Hello,

I have a small server running 8.04 that I mainly use for web testing, mlnet and backups.

It is completely headless and I manage it through ssh. However there are two little things that I would like to change on it and don't know how.

First I would like it to beep when it has finished booting up, this way it would be easier for me to know when I can ssh to it.

The second one is that I would like it to power down when I press the power button. Currently it doesn't do anything, and sometimes I have to start another PC just to turn it off.

Does somebody know how to accomplish this?

Thanks!

---

### Post by cackles on 2008-05-19
```
sudo apt-get install beep
sudo nano /etc/rc.local
```

insert

```
beep -r 5
```

before end and thats that. BTW you can configure 'beep' beep --help for commands after you get it.

And the powerbutton issue is probably in your BIOS. Have you tried holding it in for around 5 secs? Theres instant off, soft off hibernate etc. thats down to your BIOS. My windows machines shut themselves down when its pressed, I could have it instant off but its a BIOS setting.

---

### Post by cdenley on 2008-05-19
> 
The second one is that I would like it to power down when I press the power button. Currently it doesn't do anything, and sometimes I have to start another PC just to turn it off.


I think this would do the trick
```

sudo apt-get install acpid

```

---

### Post by Amt0571 on 2008-05-19
Thanks!

It worked perfectly!

---

