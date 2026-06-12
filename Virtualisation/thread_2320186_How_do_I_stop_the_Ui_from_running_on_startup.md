---
title: "How do I stop the Ui from running on startup?"
date: 2016-04-11
forum: Virtualisation
---

### Post by mattig89ch on 2016-04-11
Hidy ho all,

I'm working on keeping some older skills I have, sharp.  And one of those skills is, or was, setting up an apache server, to run a website.  Now I did this 9 or 10 years ago, and last I heard, that server was still hosting the website.  Though I have fallen out of touch with that place, so it could have been replaced by now.

Now, I managed to setup a new apache server, recently.  But while I was asking questions on that topic, it was pointed out to me that most web servers only run their cli, to save resources for the actual website hosting.  So, I decided to try and stop the ui from running on a vm of Ubuntu 15.10 (32 bit).  And disable its ui completely, so I only have the cli to work with.  Then setup the server again, that way.

Only trouble is, the Ui doesn't seem to want to be disabled.  I followed [these]("http://www.htpcbeginner.com/force-ubuntu-boot-into-terminal/") instructions, but the ui is still appearing at startup.  Is there a way to simply stop the user interface from running at startup?  Or do I have to remove it completely?  If its the latter, then how do I go about removing the user interface from an Ubuntu desktop?

---

### Post by MAFoElffen on 2016-04-11
The link you posted would be the easiest and most direct way to do what you are trying to do is to boot your vm up in text console mode (without the GUI even loading up). That would give you the security you are looking for (X not in the picture at all) and regain the resources you are looking for (X not loaded, so not using any resources at all). That solution was "exactly" what I was thinking of as I was reading your post, before even following the link and reading that.

If it is still coming up as X, ensure that /etc/default/grub is passing the "text" kernel boot option, and rerun:
```

sudo update-grub

```
It needs to run that, which picks up the defaults from that file, when it generates grub.cfg.

There is another way to force that, which would force the default rc init state to init 3, which would be text console multi-user mode. If the above does not work for you, then I'll pst instructions on how to do that...

---

### Post by sudodus on 2016-04-11
The boot option **text** does not work for me in newer systems.

I found this link: [How to boot into command line on Ubuntu or Debian](http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html)

and it seems you need the following command line too (unless maybe if you switch to booting via ***init*** instead of ***systemd***)

```
sudo systemctl set-default multi-user.target
```

Please let us know if it works for you :-)

---

### Post by mattig89ch on 2016-04-11
Just about to post back.  The first method didn't do anything for me.  But the second seems to have done the trick.

Thanks for the help all!

---

