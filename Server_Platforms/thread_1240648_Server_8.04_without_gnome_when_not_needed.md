---
title: "Server 8.04 without gnome when not needed?"
date: 2009-08-14
forum: Server Platforms
---

### Post by sefs on 2009-08-14
Hi all,

I have a 8.04 Server running that boots up to the gnome login screen.  I did that so that I could configure the server easily via gui.

Now I want it to run without the gui interface.  But I would like to be still able to run the gui easily if I ever need to configure anything.

How can I set up so it boots up in "termainal" mode.  But If i ever need the gui, I can easily log in and runt a command to start the gui that would then start and be like the server with the gui as i presently have it.

Thanks.

---

### Post by Ram-Z on 2009-08-14
Have a look at this:

[http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/)

---

### Post by jocampo on 2009-08-14
> **sefs said:**
> Hi all,

I have a 8.04 Server running that boots up to the gnome login screen.  I did that so that I could configure the server easily via gui.

Now I want it to run without the gui interface.  But I would like to be still able to run the gui easily if I ever need to configure anything.

How can I set up so it boots up in "termainal" mode.  But If i ever need the gui, I can easily log in and runt a command to start the gui that would then start and be like the server with the gui as i presently have it.

Thanks.

Do this

```
cd /etc/rc3.d
```
```
sudo mv S30gdm K70gdm
```

To understand why you shall do it like this enter

```
cat /etc/rc3.d/README
``` and you'll get it.

---

### Post by sefs on 2009-08-15
Yup that works. Thanks alot.

One last question though. If I go startx and the gdm starts.  Is there a way to stop it and go back to the text based stuff without having to reboot?

Or should I just reboot after finishing with the gdm if i need to use it.

Thanks.

Update:  I notice that if I logout using the gdm it takes me back to the termnial prompt from there, and then if i type log out there it takes me back to a terminal login screen.  So I believe thats it?

---

### Post by Iowan on 2009-08-15
I don't have **gdm** on my server, but check */etc/init.d*. It *might* be possible to stop via **/etc/init.d/gdm stop** if it exists. You can check the */etc/rc3.d/K70gdm* script to see what it does.

---

