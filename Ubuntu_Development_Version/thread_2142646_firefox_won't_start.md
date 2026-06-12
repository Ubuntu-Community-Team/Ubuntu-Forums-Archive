---
title: "firefox won't start"
date: 2013-05-06
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-05-06
FireFox web-browswer will not start after update and hard reboot from <restore> of tabs after startup. Opening screen will pop up but as soon as you click <restore> it will crash out with no warnings.

Anybody else?

---

### Post by Azyx on 2013-05-06
As I understand it, firefox will start, but when you try to restore it crash? Or?

There is a common way to sometimes get little info way an application crash and it is to start the application from terminal.

Open terminal and type :

firefox

and hit enter.

There you can get a response on why firefox crashes and copy the output in the terminal, and maybe someone can help you.

/Cheers

PS. Have you run a second update, after reboot? Sometimes when you have a kernel-update, you may need a second update after reboot i think.

---

### Post by ventrical on 2013-05-06
> **Azyx said:**
> As I understand it, firefox will start, but when you try to restore it crash? Or?

There is a common way to sometimes get little info way an application crash and it is to start the application from terminal.

Open terminal and type :

firefox

and hit enter.

There you can get a response on why firefox crashes and copy the output in the terminal, and maybe someone can help you.

/Cheers

PS. Have you run a second update, after reboot? Sometimes when you have a kernel-update, you may need a second update after reboot i think.

Ok.. thanks.

```

ventrical@ventrical-AcerAMD64bitDual:~$ firefox


(process:2752): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Terminated
ventrical@ventrical-AcerAMD64bitDual:~$ 

```

I terminated  it in system monitor <end process>.

---

### Post by Azyx on 2013-05-06
> **ventrical said:**
> Ok.. thanks.

```

ventrical@ventrical-AcerAMD64bitDual:~$ firefox


(process:2752): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed
Terminated
ventrical@ventrical-AcerAMD64bitDual:~$ 

```

I terminated  it in system monitor <end process>.

With google and error-message I find this:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1166514](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1166514)

Do you run 13:10?

Cheers

---

### Post by mc4man on 2013-05-06
> **ventrical said:**
> FireFox web-browswer will not start after update and hard reboot from <restore> of tabs after startup. Opening screen will pop up but as soon as you click <restore> it will crash out with no warnings.

Anybody else?
Assuming you mean the 'this is embarrassing.." screen when one restarts with firefox open. I haven't seen this particular mis-behavior with ff though I usually never have that many tabs open.

(- My biggest issue with ff is that at least 2-3 times a day when I close ff the window closes but the ff process doesn't.
killall firefox is becoming one of my most used commands, this has been going on for some time...

---

### Post by ventrical on 2013-05-07
> **mc4man said:**
> Assuming you mean the 'this is embarrassing.." screen when one restarts with firefox open. I haven't seen this particular mis-behavior with ff though I usually never have that many tabs open.

(- My biggest issue with ff is that at least 2-3 times a day when I close ff the window closes but the ff process doesn't.
killall firefox is becoming one of my most used commands, this has been going on for some time...


Yes.. and then I click <restore> and now = crash .. but process is still running.  I like keeping open TABS because I am just way too busy and that feature is a downtime saver for me.

Also process is running  shown in system monitor.

Thanks mac4man.

---

### Post by ventrical on 2013-05-07
> **Azyx said:**
> With google and error-message I find this:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1166514](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1166514)

Do you run 13:10?

Cheers


Of course I do. This is Ubuntu +1

```

ventrical@ventrical-AcerAMD64bitDual:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Saucy Salamander (development branch)
Release:	13.10
Codename:	saucy
ventrical@ventrical-AcerAMD64bitDual:~$ 



```

Thanks for digging up that old raring bug report. I have had this convert btrfs install for several weeks now and now may be a good time to test the restore option. I'm just not sure why all of a sudden this behaviour.

---

### Post by ventrical on 2013-05-07
> **mc4man said:**
> Assuming you mean the 'this is embarrassing.." screen when one restarts with firefox open. I haven't seen this particular mis-behavior with ff though I usually never have that many tabs open.

(- My biggest issue with ff is that at least 2-3 times a day when I close ff the window closes but the ff process doesn't.
killall firefox is becoming one of my most used commands, this has been going on for some time...

@mc4man,

  It WAS the tabs!!. Too many tabs... Thanks for the hint.

 Thanks everybody.

---

