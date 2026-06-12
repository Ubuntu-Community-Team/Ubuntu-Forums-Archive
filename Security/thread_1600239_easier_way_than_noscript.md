---
title: "easier way than noscript?"
date: 2010-10-18
forum: Security
---

### Post by ventrical on 2010-10-18
I'm just wondering if there is an easier way to filter out javascript code from Firefox's adress bar other than using java's noscript.

  I do notice that  there is an  traffic cop (do_wait) at the end of an incomplete script.

So I am just wondering if others have any ideas on how to lock this down.

---

### Post by SeijiSensei on 2010-10-19
You could install Adblock Plus in Firefox and add a custom rule to block all files ending in .js.

---

### Post by ventrical on 2010-10-19
> **SeijiSensei said:**
> You could install Adblock Plus in Firefox and add a custom rule to block all files ending in .js.


 I am trying to discern a filter for the navigator adress bar in Firefox browser.

ahh.. it just came to me...

---

### Post by ventrical on 2010-10-19
Here is some Mozilla info.  Looks like a patch-fix. if you go to adobe home page for a plug-in check you will be notifed of the security hole if you do not have the update.

---

### Post by ventrical on 2010-10-19
Nope ! The new update does not fix the security hole in the address bar.

---

### Post by OpSecShellshock on 2010-10-19
You're talking specifically about javascript that runs due to being part of the URL in the address bar? The easiest way to stop that would be to not click on any buttons or links that run those scripts. Sometimes that can be hard to know either due to code obfuscation or due to really long URLs where you can't see all the way to the end of it when hovering over the link or something. Honestly I wasn't aware that a site that was forbidden by NoScript to run scripts could still be made to do so by putting it into the address bar directly. Do you have an example of a site where this happens?

---

### Post by ventrical on 2010-10-20
> **OpSecShellshock said:**
> You're talking specifically about javascript that runs due to being part of the URL in the address bar? The easiest way to stop that would be to not click on any buttons or links that run those scripts. Sometimes that can be hard to know either due to code obfuscation or due to really long URLs where you can't see all the way to the end of it when hovering over the link or something. Honestly I wasn't aware that a site that was forbidden by NoScript to run scripts could still be made to do so by putting it into the address bar directly. Do you have an example of a site where this happens?

You can check out this thread and the poster that raised the question about the security hole.

[http://ubuntuforums.org/showthread.php?t=1599181](http://ubuntuforums.org/showthread.php?t=1599181)

 In the wild, radomly , it has not happened, but , there is still the potential for this to happen. I think it would be a very rare case (or perhaps not) , but, the point is that Firefox has a serious hole that I was not aware of until it was brought to my attention.

  I would assume then that Comodo safe surf or link scanner  on conventional windows may block such script ... but .. I am just about to give that a try.

---

### Post by uRock on 2010-10-20
What about NoScript makes it hard to protect your system? I have been using NoScript for a long time and have had no problems with it.

You can also protect your system by running the AppArmor profile for Firefox.

---

### Post by ventrical on 2010-10-20
The same  thing happene in IE, it will lock right up and you can only get out by ending IE in taskmanager.

---

### Post by ventrical on 2010-10-20
> **uRock said:**
> What about NoScript makes it hard to protect your system? I have been using NoScript for a long time and have had no problems with it.
 
You can also protect your system by running the AppArmor profile for Firefox.
 
  Do you have a few quick instructions on how to do this?
 
Thanks in advance.

---

### Post by uRock on 2010-10-20
[Intro to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

---

### Post by OpSecShellshock on 2010-10-20
So it turns out that NoScript still seems to be the easiest way to do this, but it's not a default setting. First, install the NoScript extension if it's not already installed. In the firefox address bar, type:

```
about:config
```

and skip the warning. In the "filter" line, type in noscript.allowURLBarJS and when the line comes up, right-click on it and select Toggle from the list to set the value to false. That should take care of it, but you can test it with the script from the other thread to be sure.

---

### Post by Rubi1200 on 2010-10-20
> **OpSecShellshock said:**
> So it turns out that NoScript still seems to be the easiest way to do this, but it's not a default setting. First, install the NoScript extension if it's not already installed. In the firefox address bar, type:

```
about:config
```and skip the warning. In the "filter" line, type in noscript.allowURLBarJS and when the line comes up, right-click on it and select Toggle from the list to set the value to false. That should take care of it, but you can test it with the script from the other thread to be sure.
Very nice tip OpSecShellshock :)

Tested and worked perfectly!

I just wonder though whether something that was crafted more maliciously could somehow bypass this?

---

### Post by OpSecShellshock on 2010-10-20
> **Rubi1200 said:**
> Very nice tip OpSecShellshock :)

Tested and worked perfectly!

I just wonder though whether something that was crafted more maliciously could somehow bypass this?

I get the impression that it applies to all javascript in the URL bar, including from trusted sites. Of course it would also remove the ability to do a quick XSS test against your own websites, but toggling it is fairly easy.

---

### Post by ventrical on 2010-10-20
> **OpSecShellshock said:**
> So it turns out that NoScript still seems to be the easiest way to do this, but it's not a default setting. First, install the NoScript extension if it's not already installed. In the firefox address bar, type:

```
about:config
```and skip the warning. In the "filter" line, type in noscript.allowURLBarJS and when the line comes up, right-click on it and select Toggle from the list to set the value to false. That should take care of it, but you can test it with the script from the other thread to be sure.

  Thanks .. works great !!

---

