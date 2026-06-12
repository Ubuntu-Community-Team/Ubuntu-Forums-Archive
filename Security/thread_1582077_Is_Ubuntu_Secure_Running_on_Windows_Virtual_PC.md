---
title: "Is Ubuntu Secure Running on Windows Virtual PC"
date: 2010-09-25
forum: Security
---

### Post by reyes99 on 2010-09-25
Hi,

I wanted to know if I install Ubuntu on my virtual PC on Windows 7 is it just as secure?  

If I have a keylogger or some spyware will that affect the session I have running on the Virtual PC?  Can they still steal my passwords?

Thanks

:guitar:

---

### Post by Fafler on 2010-09-26
I'm not sure what you're talking about here. Is it keyloggers on the host or the virtual machine?

Anyway, a keylogger on the virtual machine will only be able to log anything from the virtual machine when it is i focus. Otherwise, none of the input from either keybord or mouse i forwarded from the host to the virtual PC.

The windows host will always be able to log any input send through it to the virtual machine. One possible way around this could be using a extra set of input devices for the virtual machine, disabling them on the host and routing the USB devices directly to the virtual machine. However, i have no idea how to do this under Windows and it's just an idea, it might have security flaws too.

---

### Post by endotherm on 2010-09-26
it is safest to assume that if the host is compromised, the guest is as well, though in all likelyhood, the malware would have to be coded specifically to attack VMs.

A few security specialists have discussed using VMs for security, but they all run a host with only the basest of software and a vmware workstation instance, and they never use it for anything except managing the VMs. that way, the guests can be restored from a clean snapshot weekly (or even daily). Here is an interview with the researcher that created the Blue Pill hypervisor rootkit. [http://www.eweek.com/c/a/Security/Rutkowska-AntiVirus-Software-Is-Ineffective/](http://www.eweek.com/c/a/Security/Rutkowska-AntiVirus-Software-Is-Ineffective/)
while the rootkit is not as undetectable as she first claimed, it does show that a rootkit can sit under the virtual hypervisor, at a very low level, and intercept any hardware command entered in the host or any of the guest.

---

### Post by rileinc on 2010-09-26
> Can they still steal my passwords?
Yes. 
If you have a keylogger on W7, it will record everything you type. 
What you run in a virtual machine changes nothing.

---

### Post by reyes99 on 2010-09-26
Thanks for your posts, 

So do you guys think it will be safer to install Linux as the main OS and run VirtualBox from within linux.  That way I have less risk of having key loggers only when I am in Windows.  

Are there any keyloggers that attack linux??

Thanks

---

### Post by Fafler on 2010-09-26
Absolutely.

It would be quite trivial to write a keylogger for Linux, but still, it's not as much a security concern, as you need to get the keylogger into the system and that is much harder.

There's a couple of rootkit detectors available in the Ubuntu repository and i think they should cover your needs.

---

### Post by OpSecShellshock on 2010-09-26
> **reyes99 said:**
> Thanks for your posts, 

So do you guys think it will be safer to install Linux as the main OS and run VirtualBox from within linux.  That way I have less risk of having key loggers only when I am in Windows.  

Are there any keyloggers that attack linux??

Thanks

I think it would be much better to have Linux as the host OS, yes. That would also allow you to only fire up the Windows VM for things that absolutely must run on Windows only (and that's not a lot of stuff, really, except for folks who play a lot of PC games).

As for the keylogger, well, they do exist, but not in the same way they do on Windows. In Linux they're for users who are installing them personally by hand and using them on purpose. There's no way I'm aware of for one to be fully installed and to run persistently in every session by a remote, malicious process.

As for rootkit detection, it's probably not worth the stress. Every output of those commands I've ever assisted with has been a false positive. Besides that, if you've got one, you wouldn't be able to trust the output of detection software anyway. Better to just back everything important up to removable media regularly and reinstall at the first sign of weirdness (which itself happens so rarely it's not really worth mentioning).

---

### Post by reyes99 on 2010-09-26
Thank you all for the great information.  

I am new to Linux but I have had it windows!!

They just stole my passwords and hacked my website and who knows what other information they have stolen like credit card info, bank account passwords...

Thanks again!!

Ralph

---

### Post by OpSecShellshock on 2010-09-26
> **reyes99 said:**
> Thank you all for the great information.  

I am new to Linux but I have had it windows!!

They just stole my passwords and hacked my website and who knows what other information they have stolen like credit card info, bank account passwords...

Thanks again!!

Ralph

In that case, if I might make a suggestion, switch your website uploads to sftp, set a complex password, update your website's software (if applicable), and contact your bank to get a new card and have them check your account for unusual activity prior to messing with operating systems.

---

