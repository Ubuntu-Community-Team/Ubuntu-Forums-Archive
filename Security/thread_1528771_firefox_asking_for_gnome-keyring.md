---
title: "firefox asking for gnome-keyring?"
date: 2010-07-11
forum: Security
---

### Post by miles916 on 2010-07-11
Hi guys!

for a while now, firefox has been prompting gnome-keyring (twice) and i have no idea why. 

there is one applet i know of on my system that wants me to enter my keyring pw twice "CPU Frequency Scaling Monitor" (i have a core2-duo cpu, a monitor for each cpu), but i have no clue why ff would be invoking a change in how ubuntu controls that app. 

is there any way of finding out, which application (or perhaps an add-on??) is actually asking for my keyring-pw (the input window just says "an application..." not like e.g. "synaptic package manager...".

thanks in advance for any tips

regards,
M.

---

### Post by wacky_sung on 2010-07-11
> for a while now, firefox has been prompting gnome-keyring (twice) and i  have no idea why. 

Are you referring to the Master Password prompt from firefox?

---

### Post by lovinglinux on 2010-07-11
There is an add-on that does that. It is  [Gnome-keyring password integration](https://addons.mozilla.org/en-US/firefox/addon/8737/).

---

### Post by wacky_sung on 2010-07-11
Most of the passwords can be crack and it all depend on the strength of passwords in which you have input.Use the below link to test the strength of your passwords.My advise is use a password with a 20 characters or more which thus making it a real pain if people just wanna crack it which may took years even with rainbow tables.

[http://www.passwordmeter.com/](http://www.passwordmeter.com/)
[http://lastbit.com/pswcalc.asp](http://lastbit.com/pswcalc.asp)

---

### Post by miles916 on 2010-07-12
> **wacky_sung said:**
> Are you referring to the Master Password prompt from firefox?

nope, thats why i think its so weird... 

> **lovinglinux said:**
> There is an add-on that does that. It is Gnome-keyring password integration.

i found that too, but i dont have it installed... (or is it part of ubuntu firefox modifications? if so, why hasnt it always asked for my keyring password?)


i think i may have found it: extension "bindwood" - an extension to synchronize your bookmarks to a local couchdb

disabled it, no keyring prompt. i just reenabled it, lets see what happens... 

yup, that was it... 

thanks for ur help guys :)

---

