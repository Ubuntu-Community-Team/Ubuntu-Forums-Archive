---
title: "[SOLVED] Can I do a safe shutdown with the power button?"
date: 2008-09-07
forum: Server Platforms
---

### Post by grs on 2008-09-07
I'm wondering about setting Ubuntu Server to shutdown safely from the power button on the case.
I had a linux based server package installed before and the following commands installed and set it up for me, will this do the same on Ubuntu Server? (with the sudo prefix of course)

```

apt-get install acpid
service acpid start

```

This would be great, the noisey server is in an empty bedroom but people stay from time to time and I'm not always there to shut it down and rather than having to give other people the password etc.

---

### Post by beniwtv on 2008-09-08
AFAIK this comes by default with Ubuntu Server, my Ubuntu server does this. When I press the power button it beeps shortly and then shuts down safely.

However, if you're logged in in a Gnome session, it will prevent it from shutting down and show the log out dialog instead (I have no GUI on the server), though there might be a way to do it.

Hope this helps.

Cheers,

---

### Post by beta.tester on 2008-09-08
> **grs said:**
> I'm wondering about setting Ubuntu Server to shutdown safely from the power button on the case.
I had a linux based server package installed before and the following commands installed and set it up for me, will this do the same on Ubuntu Server? (with the sudo prefix of course)

```

apt-get install acpid
service acpid start

```

This would be great, the noisey server is in an empty bedroom but people stay from time to time and I'm not always there to shut it down and rather than having to give other people the password etc.

Hi

I hope I haven't  misunderstood what you are trying to do but to shutdown you can type (In either term or another terminal (CTRL-ALT-F3 say))

sudo shutdown -h now    (This shuts down the machine)
sudo shutdown -r now    (This restarts the machine)

You will of course be prompted for your password ;)

Kind regards    john

---

### Post by grs on 2008-09-08
You have misunderstood me as I said above:-

This would be great, the noisey server is in an empty bedroom but people stay from time to time and I'm not always there to shut it down and rather than having to give other people the password etc.

I know how to shutdown with commands.
My Ubuntu Server must not have acpid running as standard. I now have it installed and running fine. Thanks

---

