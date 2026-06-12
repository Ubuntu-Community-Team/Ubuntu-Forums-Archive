---
title: "Struggling with Apparmor and Firefox"
date: 2013-01-17
forum: Security
---

### Post by Paddy Landau on 2013-01-17
I am attempting to enable Apparmor for Firefox, but being very new to Apparmor, I have got myself stuck.

I am running Ubuntu 12.04 64-bit fully updated, and default Firefox from the repositories.

Here is what I did:

[LIST=1]
[*]Installed [FONT=Lucida Console]apparmor-profiles[/FONT].
[*][FONT=Lucida Console]sudo aa-enforce /etc/apparmor.d/usr.bin.firefox[/FONT]
[/LIST]
At this point, [FONT=Lucida Console]sudo[/FONT] [FONT=Lucida Console]apparmor[/FONT] [FONT=Lucida Console]status[/FONT]  reported Firefox in enforce mode.

However, I hit a small snag. I  attempt to open a file that is being downloaded (see [screen-shot]("http://ubuntuforums.org/attachment.php?attachmentid=230186&d=1358439390")). But, it  no longer opens the file; it downloads but does not open. I presumed that it was because my temporary folder is not  [FONT=Lucida Console]/tmp[/FONT] but [FONT=Lucida Console]~/.tmp[/FONT]. So, I edited the Firefox profile ([FONT=Lucida Console]/etc/apparmor.d/usr.bin.firefox[/FONT]) and added the following two lines:
```
  owner @{HOME}/.tmp/** m,
  @{HOME}/.tmp/.X[0-9]*-lock r,
```Alas, it still didn't work. So, I wanted to disable the profile, to check whether or not my problem was coincidence. I thought that setting the profile to complain mode would do the trick:
```
sudo aa-complain /etc/apparmor.d/usr.bin.firefox
```Alas again, now I have the profile in both complain and enforce mode!

Please help me:

[LIST]
[*]How do I disable the profile?
[*]How do I get the open function working again with the profile enforced?
[/LIST]

---

### Post by bodhi.zazen on 2013-01-17
Take a quick look at the commands here:

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

restart both apparmor and firefox after making profile changes.

If you still have a problem, post the errors from the logs.

---

### Post by samiux on 2013-01-17
> **Paddy Landau said:**
> I am attempting to enable Apparmor for Firefox, but being very new to Apparmor, I have got myself stuck.

I am running Ubuntu 12.04 64-bit fully updated, and default Firefox from the repositories.

Here is what I did:

[LIST=1]
[*]Installed [FONT=Lucida Console]apparmor-profiles[/FONT].
[*][FONT=Lucida Console]sudo aa-enforce /etc/apparmor.d/usr.bin.firefox[/FONT]
[/LIST]
At this point, [FONT=Lucida Console]sudo[/FONT] [FONT=Lucida Console]apparmor[/FONT] [FONT=Lucida Console]status[/FONT]  reported Firefox in enforce mode.

However, I hit a small snag. I  attempt to open a file that is being downloaded (see [screen-shot]("http://ubuntuforums.org/attachment.php?attachmentid=230186&d=1358439390")). But, it  no longer opens the file; it downloads but does not open. I presumed that it was because my temporary folder is not  [FONT=Lucida Console]/tmp[/FONT] but [FONT=Lucida Console]~/.tmp[/FONT]. So, I edited the Firefox profile ([FONT=Lucida Console]/etc/apparmor.d/usr.bin.firefox[/FONT]) and added the following two lines:
```
  owner @{HOME}/.tmp/** m,
  @{HOME}/.tmp/.X[0-9]*-lock r,
```Alas, it still didn't work. So, I wanted to disable the profile, to check whether or not my problem was coincidence. I thought that setting the profile to complain mode would do the trick:
```
sudo aa-complain /etc/apparmor.d/usr.bin.firefox
```Alas again, now I have the profile in both complain and enforce mode!

Please help me:

[LIST]
[*]How do I disable the profile?
[*]How do I get the open function working again with the profile enforced?
[/LIST]

You need to replace the following two lines :

```
  owner /tmp/** m,
  /tmp/.X[0-9]*-lock r,
```

with :

```
  owner @{HOME}/.tmp/** m,
  @{HOME}/.tmp/.X[0-9]*-lock r,
```

instead of adding them.

In addition, please make sure that /tmp/ is completely replaced by ~/.tmp/.
(Hints : /etc/fstab)

The user manual of Apparmor is [here]("https://help.ubuntu.com/community/AppArmor").

Ah, forgot to tell you that you need to install the following in order to use the Apparmor commands :

```
sudo apt-get install apparmor-utils
```

By the way, in term of security, please do not use Adobe Reader 9 as it has known vulnerabilities.

Samiux

---

### Post by vasa1 on 2013-01-17
> **bodhi.zazen said:**
> Take a quick look at the commands here:

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

restart both apparmor and firefox after making profile changes.

If you still have a problem, post the errors from the logs.

Hi bodhi.zazen, great to see you here :)

---

### Post by vasa1 on 2013-01-17
> **Paddy Landau said:**
> ..., now I have the profile in both complain and enforce mode!
...
Did you change from enforce to complain (or the other way) while Firefox was open?

And, instead of editing profiles by hand, why don't you use "sudo aa-logprof"?

---

### Post by Paddy Landau on 2013-01-18
Thank you for all of your replies. I appreciate them.

[SIZE=3]First, I'll answer you individually…[/SIZE]

> **bodhi.zazen said:**
> Take a quick look at the commands here:
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
I did, initially, but it seemed to be dated because I got stuck on one point quite early (I forget which point, sorry).

> **samiux said:**
> You need to replace the following two lines :
```
  owner /tmp/** m,
  /tmp/.X[0-9]*-lock r,
```with :
```
  owner @{HOME}/.tmp/** m,
  @{HOME}/.tmp/.X[0-9]*-lock r,
```instead of adding them.
In addition, please make sure that /tmp/ is completely replaced by ~/.tmp/.
(Hints : /etc/fstab)
I have a problem with this approach. This would not work for other users on this system. Is there no way to specify both [FONT=Lucida Console]/tmp[/FONT] and [FONT=Lucida Console]~/.tmp[/FONT]? Or, even better, to specify [FONT=Lucida Console]~/.tmp[/FONT] only if the user has such a folder, otherwise [FONT=Lucida Console]/tmp[/FONT]?

I use [FONT=Lucida Console]~/.tmp[/FONT] because my home folder   is encrypted, so it creates extra security. However, not all users do   this. I have set my temporary files to [FONT=Lucida Console]~/.tmp[/FONT] by adding the following lines to [FONT=Lucida Console]/etc/profile[/FONT]:
```
if [ -d "${HOME}"/.tmp ]
then
        export TMP="${HOME}"/.tmp
        export TEMP="${HOME}"/.tmp
        export TMPDIR="${HOME}"/.tmp
fi
```I have temporarily done as you ask in [FONT=Lucida Console]usr.bin.firefox[/FONT] (but not in [FONT=Lucida Console]/etc/fstab[/FONT], though) to see what works.

> **samiux said:**
> The user manual of Apparmor is here.
Thank you; that has been most helpful.

> **samiux said:**
> By the way, in term of security, please do not   use Adobe Reader 9 as it has known vulnerabilities.
Oh… but version 10 is not available to Linux. I really do prefer Adobe   to Evince for several reasons, especially when printing. Any   suggestions?

> **vasa1 said:**
> Did you change from enforce to complain (or the other way) while Firefox was open?
I think that must have been my problem. That problem has gone away today.

> **vasa1 said:**
> And, instead of editing profiles by hand, why don't you use "sudo aa-logprof"?
Hmm, I did not know about it! Thanks for pointing it out. However, I   have been reading the manual and trying to run it, but I am utterly   lost! I do not understand how to use it.

[SIZE=3]Now, I'll give what has happened…[/SIZE]

**Experiment 1**

I made the change to [FONT=Lucida Console]usr.bin.firefox[/FONT] as Samiux suggested; reloaded the profile; restarted Firefox.

Unfortunately, I still have the problem.

I disabled the profile and restarted Firefox; and it works correctly again.

So…

**Experiment 2**

I reverted my [FONT=Lucida Console]~/.tmp[/FONT] back to the normal [FONT=Lucida Console]/tmp[/FONT] (both [FONT=Lucida Console]/etc/profile[/FONT] and [FONT=Lucida Console]usr.bin.profile[/FONT], and logged out and in again), with the Apparmor profile disabled. Firefox works as expected.

I re-enabled the profile; and, sadly, again the download does not open Adobe. (I have also checked this with a Libre Office document, and the same problem happens.) :(

So, [FONT=Lucida Console]~/.tmp[/FONT] was a red herring. For now, I'll leave [FONT=Lucida Console]/tmp[/FONT] as is.

What next?

---

### Post by Paddy Landau on 2013-01-18
Silly me &#8212; I forgot to look at the logs.

Here are the lines posted in [FONT=Lucida Console]/var/log/kern.log[/FONT] when I attempt to open the PDF document from the download dialogue.
```
Jan 18 11:33:54 Daisy kernel: [  163.325601] type=1400 audit(1358508834.268:58): apparmor="DENIED" operation="exec" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper" name="/opt/Adobe/Reader9/Reader/intellinux/bin/acroread" pid=5768 comm="acroread" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
```Also, I noticed a line that shows when I first open Firefox:
```
Jan 18 11:33:08 Daisy kernel: [  117.893057] type=1400 audit(1358508788.835:57): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/etc/apt/sources.list" pid=4465 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```Surely that should not happen?

** EDIT 1:**

It gets worse! The profile is even preventing me from uploading screen-shots into Ubuntu Forums!
```
Jan 18 12:38:10 Daisy kernel: [ 4019.503753] type=1400 audit(1358512690.443:62): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name=2F7075626C69632F43686F6F73696E67206170706C69636174696F6E2E706E67 pid=4465 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=65534
```For now, I have disabled the Firefox profile, so that I can continue to do what I need to do.

Perhaps I need to completely disable and remove Apparmor and all of its settings, then reinstall? If so, how do I go about it?

**EDIT 2:**

I have enabled this profile on another 12.04 system (which does not use [FONT=Lucida Console]~/.tmp[/FONT]). It has the same problem with the downloads! [very sad face]

---

### Post by vasa1 on 2013-01-18
> **Paddy Landau said:**
> ...

Hmm, I did not know about it! Thanks for pointing it out. However, I   have been reading the manual and trying to run it, but I am utterly   lost! I do not understand how to use it.
...
The early part of **man aa-logprof** is relatively easy to understand. Do take a look at it. Once you get the hang of it, I think you won't need to look at the logs anymore. aa-logprof will do that for you.

Overall, your usage seems quite complex! Mine is simple with no encryption and just the one user. All the best.

By the way, you may want to look at some links I referred to [here]("http://askubuntu.com/a/236429/25656").

---

### Post by samiux on 2013-01-18
> **Paddy Landau said:**
> Silly me — I forgot to look at the logs.

Here are the lines posted in [FONT=Lucida Console]/var/log/kern.log[/FONT] when I attempt to open the PDF document from the download dialogue.
```
Jan 18 11:33:54 Daisy kernel: [  163.325601] type=1400 audit(1358508834.268:58): apparmor="DENIED" operation="exec" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper" name="/opt/Adobe/Reader9/Reader/intellinux/bin/acroread" pid=5768 comm="acroread" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
```Also, I noticed a line that shows when I first open Firefox:
```
Jan 18 11:33:08 Daisy kernel: [  117.893057] type=1400 audit(1358508788.835:57): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/etc/apt/sources.list" pid=4465 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```Surely that should not happen?

** EDIT 1:**

It gets worse! The profile is even preventing me from uploading screen-shots into Ubuntu Forums!
```
Jan 18 12:38:10 Daisy kernel: [ 4019.503753] type=1400 audit(1358512690.443:62): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name=2F7075626C69632F43686F6F73696E67206170706C69636174696F6E2E706E67 pid=4465 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=65534
```For now, I have disabled the Firefox profile, so that I can continue to do what I need to do.

Perhaps I need to completely disable and remove Apparmor and all of its settings, then reinstall? If so, how do I go about it?

**EDIT 2:**

I have enabled this profile on another 12.04 system (which does not use [FONT=Lucida Console]~/.tmp[/FONT]). It has the same problem with the downloads! [very sad face]

I would like to know if you are using the default Firefox apparmor rules from the Ubuntu or not?

If you are using default Firefox apparmor rules, it should not have any problem.

Samiux

---

### Post by Paddy Landau on 2013-01-19
> **vasa1 said:**
> The early part of **man aa-logprof** is relatively easy to understand.
Well, the manual says that [FONT=Lucida Console]aa-logprof[/FONT] is an interactive command. But when I start it, [FONT=Lucida Console]aa-logprof[/FONT] gives a couple of messages, thinks for a few seconds, and ends. So, I really don't know what to do with the application.

> **vasa1 said:**
> By the way, you may want to look at some links I referred to [here]("http://askubuntu.com/a/236429/25656").
Thanks. It makes interesting reading, but still does not solve my problem.

I feel like such a dummy with Apparmor — I really am not understanding it!

> **samiux said:**
> I would like to know if you are using the default Firefox apparmor rules from the Ubuntu or not?
Yes, I simply installed [FONT=Lucida Console]apparmor-profiles[/FONT] and enabled [FONT=Lucida Console]usr.bin.firefox[/FONT] in enforce mode (confirmed with [FONT=Lucida Console]sudo[/FONT] [FONT=Lucida Console]apparmor_status[/FONT]). I made no changes to the profile (I have undone the changes that I originally made with [FONT=Lucida Console]/tmp[/FONT]).

What I really need to do is fix the Firefox profile such that:

[LIST=1]
[*]I can open a file instead of just downloading it. If this step cannot be easily done, OK, I could live without it, because I can still download.
[*][s]Allow me to upload files, which I cannot do with the profile.[/s]
[/LIST]
[s]In your quote, vasa1, it says, "It is a distribution choice to not break [the browser] with too-aggressive security protections." Unfortunately, especially regarding uploads, it has broken it![/s]

**EDIT:** For whatever reason, uploads have started to work again today.

---

### Post by samiux on 2013-01-19
> **Paddy Landau said:**
> Well, the manual says that [FONT=Lucida Console]aa-logprof[/FONT] is an interactive command. But when I start it, [FONT=Lucida Console]aa-logprof[/FONT] gives a couple of messages, thinks for a few seconds, and ends. So, I really don't know what to do with the application.


Thanks. It makes interesting reading, but still does not solve my problem.

I feel like such a dummy with Apparmor &#8212; I really am not understanding it!


Yes, I simply installed [FONT=Lucida Console]apparmor-profiles[/FONT] and enabled [FONT=Lucida Console]usr.bin.firefox[/FONT] in enforce mode (confirmed with [FONT=Lucida Console]sudo[/FONT] [FONT=Lucida Console]apparmor_status[/FONT]). I made no changes to the profile (I have undone the changes that I originally made with [FONT=Lucida Console]/tmp[/FONT]).

What I really need to do is fix the Firefox profile such that:

[LIST=1]
[*]I can open a file instead of just downloading it. If this step cannot be easily done, OK, I could live without it, because I can still download.
[*][s]Allow me to upload files, which I cannot do with the profile.[/s]
[/LIST]
[s]In your quote, vasa1, it says, "It is a distribution choice to not break [the browser] with too-aggressive security protections." Unfortunately, especially regarding uploads, it has broken it![/s]

**EDIT:** For whatever reason, uploads have started to work again today.

I think I can answer you that why you can download the pdf but not opening it.  Please see this [link]("https://addons.mozilla.org/en-US/firefox/blocked/p156").

Samiux

---

### Post by Paddy Landau on 2013-01-19
Sigh. I just do not understand Apparmor.

I thought that perhaps the Apparmor profile for Firefox was not permitting Firefox to open Adobe Reader. So, as an experiment, I added the following rule to [FONT=Lucida Console]usr.bin.firefox[/FONT].
```
/usr/bin/acroread Pix,
```No doubt the Apparmor experts are laughing at me, because naturally it didn't work. I am utterly stumped and don't know how to proceed.

I have reverted the profile to its default. For now, I'll have to live without the ability to open a downloaded file from Firefox.

---

### Post by Paddy Landau on 2013-01-19
> **samiux said:**
> I think I can answer you that why you can download the pdf but not opening it.  Please see this [link]("https://addons.mozilla.org/en-US/firefox/blocked/p156").
Thanks, but I don't think that's the reason.

I can open the PDF with Adobe when the Apparmor profile is disabled.

When the profile is enabled, I am prevented from opening not only a PDF file with Adobe, but also an Open Office file with Libre Office.

However, I have just discovered that I can open a PDF with Evince. Hmm…

---

### Post by samiux on 2013-01-19
> **Paddy Landau said:**
> Thanks, but I don't think that's the reason.

I can open the PDF with Adobe when the Apparmor profile is disabled.

When the profile is enabled, I am prevented from opening not only a PDF file with Adobe, but also an Open Office file with Libre Office.

However, I have just discovered that I can open a PDF with Evince. Hmm&#8230;

If my memory is correct, OpenOffice and LibreOffice require Java to run.

Samiux

---

### Post by Paddy Landau on 2013-01-19
> **samiux said:**
> If my memory is correct, OpenOffice and LibreOffice require Java to run.
Does Apparmor prevent Java?

I disabled Java in Libre Office, but still I cannot open a downloaded file in Libre Office.

But here's a commonality: Both Adobe and Libre Office are installed within [FONT=Lucida Console]/opt[/FONT]. Evince, on the other hand, is not.

Perhaps [FONT=Lucida Console]/opt[/FONT] is somehow disabled?

---

### Post by samiux on 2013-01-19
> **Paddy Landau said:**
> Does Apparmor prevent Java?

I disabled Java in Libre Office, but still I cannot open a downloaded file in Libre Office.

But here's a commonality: Both Adobe and Libre Office are installed within [FONT=Lucida Console]/opt[/FONT]. Evince, on the other hand, is not.

Perhaps [FONT=Lucida Console]/opt[/FONT] is somehow disabled?

To make it easy for troubleshooting, I suggest you to disable the Apparmor and unload the profile.  If the problem is still there, the problem is not on the Apparmor.

Samiux

---

### Post by Paddy Landau on 2013-01-19
> **samiux said:**
> To make it easy for troubleshooting, I suggest you to disable the Apparmor and unload the profile.  If the problem is still there, the problem is not on the Apparmor.
I have already done that, several times.

With the profile disabled, everything works perfectly.

It is only when the profile is activated that I get the problem.

---

### Post by samiux on 2013-01-19
> **Paddy Landau said:**
> I have already done that, several times.

With the profile disabled, everything works perfectly.

It is only when the profile is activated that I get the problem.

Would you please give me the link where you download the LibreOffice file and I will test it at my side?

Samiux

---

### Post by Paddy Landau on 2013-01-19
> **samiux said:**
> Would you please give me the link where you download the LibreOffice file and I will test it at my side?
From the [official Libre Office download page]("http://www.libreoffice.org/download/").

I do appreciate the time that you are spending.

---

### Post by samiux on 2013-01-19
> **Paddy Landau said:**
> From the [official Libre Office download page]("http://www.libreoffice.org/download/").

I do appreciate the time that you are spending.

The page allows me to download tarred files or iso only.  It cannot be opened by LibreOffice, I think.

**Edit :**

Okay, I find this [page]("http://www.libreoffice.org/get-help/documentation/") can download LibreOffice format files.  I can download it from Firefox and it automatically opened by LibreOffice at my side with Apparmor for Firefox enabled.

Samiux

---

### Post by Paddy Landau on 2013-01-19
Sorry, Samiux. If you click on those, they are compressed .deb files.

Never mind.

I tried[ the page]("http://www.libreoffice.org/get-help/documentation/") you gave, but I still get the same error with both Libre Office and Adobe.

I'll see if I can find answers on other forums. If I do, I'll post back here. If I understood Apparmor better, I guess I could find the answer.

In file [FONT=Lucida Console]abstractions/ubuntu-browsers.d/productivity[/FONT], which is included into Firefox's profile, I spotted the following line:
```
/opt/Adobe/Reader9/bin/acroread Cxr -> sanitized_helper,
```So it seems that Adobe is supposed to be permitted.

I tried with Firefox in Safe Mode, but still I get the problem.

I can only guess that there is something odd about my set-up. Sigh.

---

