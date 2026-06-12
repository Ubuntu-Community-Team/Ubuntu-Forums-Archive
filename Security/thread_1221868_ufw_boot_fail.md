---
title: "ufw boot fail"
date: 2009-07-24
forum: Security
---

### Post by automaton26 on 2009-07-24
I boot without splash screen, and during about 30% of the start-ups I see a red [fail] for ufw.

The messages are always about iptables, but are often different. I can still connect OK, and if I look at gufw it just says *Firewall enabled* as normal.

1) How can I get this output, so I can post it here, as it doesn't appear in /var/log/message ? (other than taking a photo!)

2) Is the ufw fail likely to be an issue or not ?

---

### Post by bodhi.zazen on 2009-07-24
Most often you will get that if you have another firewall config tool running (such as firestarter or similar).

You can see your rules with ```
sudo ufw status
sudo iptables -L -v
```

Logs are in /var/logs/dmesg

---

### Post by automaton26 on 2009-07-25
Perhaps I tried firestarter, but then removed it and started using gufw instead - the output from *iptables -L* didn't look particularly standard.

So I've used gufw to disable the firewall, and then immediately re-enable it. Now the output from *iptables -L* looks more straightforward.

I'll keep an eye on what happens during boot from now on. Although the contents of /var/log/dmesg never contained the output I saw during boot, so I'm not sure if it's possible to get the exact [fail] text.

Thanks for your help.

---

### Post by bodhi.zazen on 2009-07-25
If you installed firestarter that is almost certainly the problem.

Probably should file a bug against firestarter, it conflicts with ufw (which is installed by default) and is not removed cleanly.

Re-install firestarter, then remove it with the purge option

```
sudo apt-get remove --purge firestarter
```

---

### Post by bodhi.zazen on 2009-07-25
I did not see the issue reported, so I filed a bug report for you.

[https://bugs.launchpad.net/ubuntu/+bug/404600](https://bugs.launchpad.net/ubuntu/+bug/404600)

---

### Post by automaton26 on 2009-07-26
Thanks for adding that launchpad bug.

I've done a restore and purge of firestarter, as you've suggested, but ufw still has a boot fail with "Resource unavailable" some of the time.

Also, after each boot (or even a manual networking restart) I can look at gufw and it claims the firewall is enabled OK, but doing *sudo ufw status* shows the status as **inactive**.

If I disable and re-enable the firewall via gufw, as mentioned previously, it then reports the status as **active** on the command-line.

So which is reporting the firewall status accurately, and which is not ?

---

### Post by bodhi.zazen on 2009-07-26
Sounds like a problem with ufw, however I am not sure what caused it.

I would purge and re-installl ufw and file a bug report.

In the bug report include the output of

sudo iptables -L -v 

when you get that error message.

---

### Post by automaton26 on 2009-07-26
OK, thanks for your advice.

For anyone else following this thread, I have purged both ufw and gufw, and reinstalled them.

However, doing this after a reboot:

```
sudo ufw status
```

still reports **inactive** (although gufw reports it as enabled), so I am manually doing the following immediately after each reboot, until I find out more:

```
sudo ufw reload
```

Because then the status on the command-line appears as **active**.

---

### Post by automaton26 on 2009-07-26
_Epilogue:_

I forgot I'd tried out the guarddog application as well as firestarter. So I purged that too, and now ufw status is correctly reported as **active** after reboot.

So basically I've done the equivalent of:

```
sudo apt-get remove --purge firestarter
sudo apt-get remove --purge guarddog
sudo apt-get remove --purge ufw
sudo apt-get remove --purge gufw
sudo apt-get install ufw
sudo apt-get install gufw
sudo ufw enable
```

The lesson is, don't try those other applications - **_gufw_** should be all you need.

It would be nice if it was part of the default ubuntu install, really.

---

