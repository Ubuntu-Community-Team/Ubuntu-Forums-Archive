---
title: "From Firestarter to Gufw"
date: 2009-08-20
forum: Security
---

### Post by oygle on 2009-08-20
I was advised in another thread to uninstall Firestarter, as it is no loner supported. That is okay with me, as it has given problems in the past. The suggestion was to install Gufw.

I recorded all the Firestarter rules and policies, then uninstalled Firestarter, then installed Gufw. Opened it up, and had to 'enable' it, seems okay. ......... BUT there are no 'rules' defined.

Yet, when I checked iptables ..

```

# sudo iptables -L -n -v

```

it showed up all the Firestarter rules, which I would expect, as Firestarter is only a Gui for iptables.

What I would like to see is those 'rules', in Gufw.

I'm able to use the internet, email, and the syslogs are showing the usual ports being blocked, so everything seems to be running okay.

It just would be nice to be able to see those rules. I notice there is an import in Gufw, but I have no idea what the format of that files is. There seems to be absolutely no documentation for Gufw.

Is there a "safe" method to remove all those (Firestarter generated) rules from iptables, and then add them with Gufw, as I notice outbound ports are being blocked ?

Thanks,

Oygle

---

### Post by sefs on 2009-08-20
This is a new one to me,

You actually saw IPTable rules within the Firestarter GUI?  (I don't mean rules that you could have add to firestarter via the gui)  

Where?

---

### Post by oygle on 2009-08-20
Sorry, what I meant was that when I displayed the iptable rules, I could 'recognise' rules that had been added 'via' Firestarter.

It would be great to 'see' those rules via Gufw.  :)

Or, somehow 'clear' or 'reset' iptables back to it's default values/rules, and then add the Gufw rules in as needed.

When I take a close look at the iptable rules, there is actually a lot of 'junk' there, as the hard drive has been moved to another computer over the years, and with Ubuntu updates, etc, there are 'old rules' that don't even apply now, like old domain names, etc.

Oygle

---

### Post by oygle on 2009-08-21
Is there a method to somehow 'clear' or 'reset' iptables back to it's default values/rules, and then add the Gufw rules in as needed ?

Oygle

---

### Post by oygle on 2009-08-21
I did an iptables -L and the Firestarter rules are not there. This must have happened after a reboot and no Firestarter. I assume all the (now) default iptables rules are "safe".

There are now UFW rules listed there, although I haven't added any. Seems everything is okay.

Oygle

---

