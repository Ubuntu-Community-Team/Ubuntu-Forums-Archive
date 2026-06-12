---
title: "Keystroke recorder"
date: 2010-03-25
forum: Security
---

### Post by jhy2a on 2010-03-25
I have two terminals setup as kiosks for users to access their benefits with. Both terminals use Ubuntu 9.10 and both are locked down using Pessulus lockdown editor as well as Squid Proxy. Each of them have 2 profiles, an administrator and a user account. The user account is the one setup to run as a kiosk. overnight, a user made several attempts to bypass the security setup on the terminals to access websites that are banned for our users. Although they were unsuccessful in bypassing the security, I need to find a keystroke or key logger program to use on these two terminals. 
 
Can anyone make any suggestions for me? I know there are several for Windows based systems but I need one for Ubuntu. I need to be able to go to the HR manager and show him that this is what is being typed in to prove malicious intent against our security measures.  Any help would be greatly appreciated.

---

### Post by OpSecShellshock on 2010-03-25
I'm not sure I understand. If you have enough information to have determined what the user was trying to do, then why do you need the specific keystrokes? Presumably you have the username of the person who was logged in at the time, as well as the site that person was trying to access. You also have physical access to the device, so you can look at anything you want on it. A keystroke logger will record everything that everybody does, not just one of the users. And in any case it sounds as though they're all administrators, so you'd need to use a hardware device. Also, regardless of whether or not you can demonstrate which sites the user was trying to get to, you seem to have evidence that the user was trying to circumvent security measures. In and of itself that ought to be sufficient for HR.

---

### Post by bodhi.zazen on 2010-03-25
> **jhy2a said:**
> I have two terminals setup as kiosks for users to access their benefits with. Both terminals use Ubuntu 9.10 and both are locked down using Pessulus lockdown editor as well as Squid Proxy. Each of them have 2 profiles, an administrator and a user account. The user account is the one setup to run as a kiosk. overnight, a user made several attempts to bypass the security setup on the terminals to access websites that are banned for our users. Although they were unsuccessful in bypassing the security, I need to find a keystroke or key logger program to use on these two terminals. 
 
Can anyone make any suggestions for me? I know there are several for Windows based systems but I need one for Ubuntu. I need to be able to go to the HR manager and show him that this is what is being typed in to prove malicious intent against our security measures.  Any help would be greatly appreciated.

Key loggers are controversial and although they have legitimate uses they have legitimate users as well and their use is illegal in some circumstances in some jurisdictions.

Because of this I am going to close this thread now.

IMO a better suggestion I would offer is to learn to use Apparmor, your security will be tighter. Use jailbash

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.local.bin.jailbash)

If you feel you need a key logger , a simple google search will give you all the information you need.

---

