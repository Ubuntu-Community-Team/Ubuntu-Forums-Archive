---
title: "Pure Text Console for the server."
date: 2010-04-28
forum: Server Platforms
---

### Post by elarrarte on 2010-04-28
[FONT=Courier New]I want to know if there is a way to disable the GUI console on 10.04 Server ... I want the traditional pure text console ... no plymouth, no plymouth-theme, just 80x24 console.

Another question, Is there a way to get those traditional messages when booting? Like 8.04 Server does?

* Starting SSH Server                           [done]
* Starting Squid Proxy Server                   [done]

Thanks!
[/FONT]

---

### Post by windependence on 2010-04-28
There's a GUI on 10.4??????? God help us I hope not. There isn't supposed to be. Is it only during startup?

-Tim

---

### Post by arrrghhh on 2010-04-28
There's no GUI on 10.04... there may be a splash screen (boot screen), but I don't have a monitor hooked up to my server, just power & network.

I think I know what you're asking, I don't remember off hand.  I think it's in the GRUB settings, you disable quiet boot or something to that effect.

---

### Post by ghost_ryder35 on 2010-04-28
comment out GRUB_CMDLINE_LINUX_DEFAULT="quiet" in /etc/default/grub
```

#GRUB_CMDLINE_LINUX_DEFAULT="quiet"

```
Then run
```

sudo update-grub

```

---

### Post by arrrghhh on 2010-04-28
That's it, thanks!

OP - please mark thread as solved if this did indeed solve your issue, thanks!

---

### Post by elarrarte on 2010-04-28
No ... there is not an easy way of booting the way 8.04 does. I ve seen that we can achieve this by modifying the configuration files under /etc/init to call the scripts under /etc/init.d instead of running the daemon directly ... but that will be a waste of time.
We have un avoid loading plymouth by moving all plymouth*.conf under /etc/init to somewhere else too ... ufffffffff :(

So, my little approach is:

 To get a pure console at grub boot menu:
GRUB_TERMINAL=console

and to get a pure console in the rest of boot process:
GRUB_CMDLINE_LINUX="nomodeset"

both values under /etc/default/grub
then, we must do: # update-grub && reboot

Thanks anyways !

---

### Post by Queue29 on 2010-04-28
> **elarrarte said:**
> No ... there is not an easy way of booting the way 8.04 does. I ve seen that we can achieve this by modifying the configuration files under /etc/init to call the scripts under /etc/init.d instead of running the daemon directly ... but that will be a waste of time.
We have un avoid loading plymouth by moving all plymouth*.conf under /etc/init to somewhere else too ... ufffffffff :(

So, my little approach is:

 To get a pure console at grub boot menu:
GRUB_TERMINAL=console

and to get a pure console in the rest of boot process:
GRUB_CMDLINE_LINUX="nomodeset"

both values under /etc/default/grub
then, we must do: # update-grub && reboot

Thanks anyways !

They put plymouth on 10.04 server? What the ****?

---

### Post by arrrghhh on 2010-04-28
> **Queue29 said:**
> They put plymouth on 10.04 server? What the ****?

Yea, now that you mention it a few times I did boot with my server plugged into my tv... and I saw a messed up boot screen.  Semi-graphical, looked horrid.  Probably going to be fixed for final, but like you said why did the put that package with the server install?  Seems I need to install the -minimal one and work my way up to what I want.  Sounds messy.

---

### Post by elarrarte on 2010-04-29
Yes ... I cannot understand why plymouth is in the server version ... I like pure text-console servers ... no plymouth or framebuffer ... those kinda things must be optional but not the default !

I cant understand these kinda decisions ... ubuntu 8.04 server is a rock and boots cleanly ... and now, 10.04, looks like OUUUUGGGGGHHHHH ... nothing serious at all and a lot of buggy messages in the boot process ... it reminds to Debian and their ugly booting process.

If we have a good boot process for the server like the 8.04 ... why we have to change it?
Why not continue that way ... ? Why waste our time chaging something that is running OK?

Another point is that ... with the old way boot method ... you can see if daemons load successfully ... and now u only have some buggy messages and the the login ... it s a pitty!! ... we re falling down!

Bye.

---

### Post by ubnutu on 2010-07-12
Here is how we restored the text console for Lucid server: 
[http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-text-console/]("http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-text-console/")

Disabled the Plymouth stuff:
[http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-disable-plymouth/]("http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-disable-plymouth/")

And got useful messages out of Upstart:
[http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-upstart/]("http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-upstart/")

Hope that is helpful.

---

### Post by joopbraak on 2010-09-29
> **ubnutu said:**
> Here is how we restored the text console for Lucid server: 
[http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-text-console/]("http://staff.adams.edu/%7Ecdmiller/posts/Ubuntu-Lucid-server-text-console/")

Disabled the Plymouth stuff:
[http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-disable-plymouth/]("http://staff.adams.edu/%7Ecdmiller/posts/Ubuntu-Lucid-server-disable-plymouth/")

And got useful messages out of Upstart:
[http://staff.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-upstart/]("http://staff.adams.edu/%7Ecdmiller/posts/Ubuntu-Lucid-server-upstart/")

Hope that is helpful.

You are a hero! Thank you.

---

