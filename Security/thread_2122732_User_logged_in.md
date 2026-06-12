---
title: "User logged in?"
date: 2013-03-06
forum: Security
---

### Post by Tinado on 2013-03-06
Hi, I have been using 64bit Ubuntu for about a year and in the past week twice my hard drive is active upon login longer than usual and so I go to reboot and a message appears saying unable to reboot (or shutdown) while users are logged in, authenticate to do so.

I am running this Ubuntu system at home so I don't want anyone else logging into my computer especially remotely!

Have I been hacked or is it a bug?

Thanks for any advice.

---

### Post by tgalati4 on 2013-03-06
Probably neither.  If you opened a Terminal in a Workspace and you used* sudo su* then you have a root terminal open.  That is another user.  If you opened Nautilus and used "Browse Files as Root" then you have another user logged on.  If you opened Synaptic or any other configuration program that requires root privilege, then you have another user logged on.  Also connecting to network shares will sometimes trigger the delayed shutdown, because you really are logged in as a another user--due to network share authentication.

Before you shutdown next time, open a terminal:

```
who -a
```

Post the results.

Mine looks like:

tgalati4@Mint14-Extensa ~/Desktop $ who -a
           system boot  2013-03-06 07:28
           run-level 2  2013-03-06 07:28
LOGIN      tty4         2013-03-06 07:28              1101 id=4
LOGIN      tty5         2013-03-06 07:28              1105 id=5
LOGIN      tty2         2013-03-06 07:28              1121 id=2
LOGIN      tty3         2013-03-06 07:28              1122 id=3
LOGIN      tty6         2013-03-06 07:28              1128 id=6
LOGIN      tty1         2013-03-06 07:28              1478 id=1
tgalati4 + tty8         2013-03-06 07:28  old         1559 (:0)
tgalati4 + pts/1        2013-03-06 07:50   .          2608 (:0.0)
tgalati4 + pts/2        2013-03-06 07:51   .          2608 (:0.0)

---

### Post by Tinado on 2013-03-06
Thanks for your reply thalati4, I was a bit shocked to learn that I had been using Ubuntu for a year without a Firewall running, apparently it's not enabled by default...

Whether I have been hacked or not and my deluxe pron stolen I have no idea either :(

And there I was congratulating myself that I had not had to reinstall Linux for a year and was not making the mistake of running as Admin lol.

I think you are probably right about it being me using an admin user programme, if so it must activate by itself because I do nothing other than login, go to make tea and return 10 minutes later to notice drive activity still.

Next time it happens I will do as you suggest and check in a terminal who is logged in.

Much appreciated thank you.

---

