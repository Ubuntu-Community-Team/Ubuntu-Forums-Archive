---
title: "Do I Need A Firewall?"
date: 2009-07-19
forum: Security
---

### Post by /usr/sbin on 2009-07-19
I dont have a firewall on my computer at the moment but i was wondering whether i actually need to use one.

Thanks Adam

---

### Post by ibutho on 2009-07-19
Linux has a built-in firewall. Its up to you whether you want to enable it or not. The tools to manage the firewall are ufw and gufw.

---

### Post by /usr/sbin on 2009-07-19
Thanks, what do those commands do? Are they both the same?

Adam

---

### Post by ibutho on 2009-07-19
The ufw tool is a CLI app that you can use to enable, disable and configure various aspects of the iptables/netfilter firewall. Gufw is a GUI frontend to ufw. Its labeled as "Firewall Configuration" in the Administration menu.

---

### Post by /usr/sbin on 2009-07-20
Thanks, what do ip tables do? Adam

---

### Post by sasho_zl on 2009-07-20
You can check out this page - [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
It shows a very easy way to configure your firewall with a script. I used it for a few months and it worked great.

---

### Post by /usr/sbin on 2009-07-20
Thank you for that.

---

### Post by Jack99 on 2009-07-20
ok so  is it worth installing "Firestarter Firewall or some other such firewall ? cos to be honest i have no idea?

so im using Ubuntu Ultimate 1.9

---

### Post by wojox on 2009-07-20
UFW is installed by default and it's command line. Firestarter is the GUI to control UFW.

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by Jack99 on 2009-07-20
> **wojox said:**
> UFW is installed by default and it's command line. Firestarter is the GUI to control UFW.

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

ahh ok thank you ...:)

---

### Post by bodhi.zazen on 2009-07-20
> **/usr/sbin said:**
> I dont have a firewall on my computer at the moment but i was wondering whether i actually need to use one.

Thanks Adam

for what ? You did not tell us anything about your system. Desktop ? router ? server ? and what do you want to do with a firewall.

This is like asking if you need an umbrella.

It results in recurring discussions and opinions.

See : **[B]Sticky:**[/B] 			                          			 			[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

If you have a more specific question, feel free to start a new thread.

---

