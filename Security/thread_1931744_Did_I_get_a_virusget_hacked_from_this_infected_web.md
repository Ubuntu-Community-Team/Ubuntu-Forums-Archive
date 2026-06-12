---
title: "Did I get a virus/get hacked from this infected website?"
date: 2012-02-26
forum: Security
---

### Post by helpme222 on 2012-02-26
Hi, I visited a website that is infected with malware in Chrome (after I visited it, I scanned it with Sucuri Scan and it IS infected). 

I had no protection in Chrome (no adblock/noscript, etc). 

I then scanned the Home folder with ClamTK and it said I have no viruses, but I was wondering, could I have been hacked? I read somewhere that if your browser gets hacked, a hacker could steal what is in your home folder. I have TONS of personal information there, so could I have been hacked?

---

### Post by OpSecShellshock on 2012-02-26
Looks like you ran across a drive-by. Most of the time those will ultimately only affect Windows systems and will attempt to install malware from a third site that is linked to from the compromised or malicious web page you went to. There is certainly nothing stopping a script or object on a page from accessing information in your home folder through the browser, but as far as I know the majority of the time that's not what these things get used for. The business model runs toward what we call a pay-per-install program where malicious actors contract out to install as much malware from others as they can manage to, on as many systems as they can. So they get paid for the installations rather than for gobbling up files directly from victim systems. This is why they tend to target the platforms with the largest installation base (Windows).

There are, of course, no guarantees that's what happened, but in my experience that's what's going on the overwhelming majority of the time with the sort of activity you've described.

To prepare for these sorts of occasions in the future, I would suggest checking the sticky posts at the top of the Security Discussions, learn how to make an Apparmor profile for your browser, and then check out Truecrypt or the like for the purpose of segmenting the sensitive information in your home folder from the stuff you don't care as much about. Also keep good backups and be prepared to re-install at a moment's notice.

---

### Post by helpme222 on 2012-02-26
> **OpSecShellshock said:**
> Looks like you ran across a drive-by. Most of the time those will ultimately only affect Windows systems and will attempt to install malware from a third site that is linked to from the compromised or malicious web page you went to. There is certainly nothing stopping a script or object on a page from accessing information in your home folder through the browser, but as far as I know the majority of the time that's not what these things get used for. The business model runs toward what we call a pay-per-install program where malicious actors contract out to install as much malware from others as they can manage to, on as many systems as they can. So they get paid for the installations rather than for gobbling up files directly from victim systems. This is why they tend to target the platforms with the largest installation base (Windows).

There are, of course, no guarantees that's what happened, but in my experience that's what's going on the overwhelming majority of the time with the sort of activity you've described.

To prepare for these sorts of occasions in the future, I would suggest checking the sticky posts at the top of the Security Discussions, learn how to make an Apparmor profile for your browser, and then check out Truecrypt or the like for the purpose of segmenting the sensitive information in your home folder from the stuff you don't care as much about. Also keep good backups and be prepared to re-install at a moment's notice.
So, is my personal data safe? And do you think I should reinstall and change all of my passwords?

---

### Post by helpme222 on 2012-02-26
Also, if I post a link to the site can you tell me if it's for ubuntu?

---

### Post by OpSecShellshock on 2012-02-26
I would caution against putting up a link to a site that leads to malware, as there are people who access this forum from Windows systems.

As to your other question, I can't be sure that your data is safe in a general sense, but I don't believe it was placed at any risk this specific time based on what you have described. There shouldn't be any need to change passwords or re-install unless you want absolute certainty that there isn't any malware.

---

### Post by helpme222 on 2012-02-26
> **OpSecShellshock said:**
> I would caution against putting up a link to a site that leads to malware, as there are people who access this forum from Windows systems.

As to your other question, I can't be sure that your data is safe in a general sense, but I don't believe it was placed at any risk this specific time based on what you have described. There shouldn't be any need to change passwords or re-install unless you want absolute certainty that there isn't any malware.
How often are facebook/youtube passwords stolen and used maliciously? Or are they not a target?

---

### Post by helpme222 on 2012-02-26
And here is the security report on the site I visited:
[http://sitecheck.sucuri.net/results/www.godlikeproductions.com/forum1/message1773268/pg1](http://sitecheck.sucuri.net/results/www.godlikeproductions.com/forum1/message1773268/pg1)

---

### Post by helpme222 on 2012-02-26
Also, I scanned that website on virustotal and it said it was clean actually, so is that site even infected after all?

---

### Post by Dry Lips on 2012-02-26
> **helpme222 said:**
> Also, I scanned that website on virustotal and it said it was clean actually, so is that site even infected after all?

I'm not sure about the site you referred to, but sometimes nasty stuff is hidden in ads that comes from a third party.

---

### Post by helpme222 on 2012-02-26
> **Dry Lips said:**
> I'm not sure about the site you referred to, but sometimes nasty stuff is hidden in ads that comes from a third party.
Can you take a look at the sucuri log for me and tell me what you think?

---

### Post by helpme222 on 2012-02-26
> **Dry Lips said:**
> I'm not sure about the site you referred to, but sometimes nasty stuff is hidden in ads that comes from a third party.
Also, I just checked and I did have adblock installed after all. But not noscript. Could adblock have blocked anything bad?

---

### Post by OpSecShellshock on 2012-02-26
The Sucuri report indicates that it's getting return codes that say the site can't be accessed at the addresses listed. If that's true all around then that means you wouldn't have been able to access those things either. I think you're OK for now. If you are using Chrome, look into an extension called NotScripts or alternatively ScriptNo.

---

### Post by helpme222 on 2012-02-26
> **OpSecShellshock said:**
> The Sucuri report indicates that it's getting return codes that say the site can't be accessed at the addresses listed. If that's true all around then that means you wouldn't have been able to access those things either. I think you're OK for now. If you are using Chrome, look into an extension called NotScripts or alternatively ScriptNo.
Thanks for the reply, I visited the site and it loaded properly, or would it have been something I couldn't have seen behind the scene?

So is the site infected or is it safe to visit?

---

### Post by helpme222 on 2012-02-26
So is the site infected after all?

---

### Post by helpme222 on 2012-02-27
Can somebody please answer?

---

### Post by OpSecShellshock on 2012-02-27
Just went to the site. I didn't do a thorough examination of the source of the page or anything, but there didn't seem to be anything malicious or suspicious when I loaded the page.

---

### Post by helpme222 on 2012-02-27
> **OpSecShellshock said:**
> Just went to the site. I didn't do a thorough examination of the source of the page or anything, but there didn't seem to be anything malicious or suspicious when I loaded the page.
So, to put my paranoid mind at rest, I am fine? :D

---

### Post by Ms. Daisy on 2012-02-27
> **OpSecShellshock said:**
> Just went to the site. I didn't do a thorough examination of the source of the page or anything, but there didn't seem to be anything malicious or suspicious when I loaded the page.
IMO that ^^^ is as good as you're going to get. 

Why are you going there if you don't trust it?

---

### Post by helpme222 on 2012-02-27
> **Ms. Daisy said:**
> IMO that ^^^ is as good as you're going to get. 

Why are you going there if you don't trust it?
I am not going to the site. I was wondering, if I remove chrome and then reinstall it, would that remove any hypothetical virus?

---

### Post by hildenbrandsteven on 2012-02-27
No, you weren't hacked. And most of those infected sites won't affect a *nix machine since they aren't compatible with the linux kernel/filesystems.

---

### Post by Ms. Daisy on 2012-02-27
Seems like you might be in panic mode.  I encourage you to calm down, take some breaths. Then very carefully re-read the responses you've gotten on this thread.  In particular I'll direct you back to what OSSS said a few posts ago because he indirectly already answered that question for you.

> **OpSecShellshock said:**
>  As to your other question, I can't be  sure that your data is safe in a general sense, but I don't believe it  was placed at any risk this specific time based on what you have  described. **There shouldn't be any need to change passwords or re-install  unless you want absolute certainty that there isn't any  malware**.

If "you're probably OK" is not going to put your mind to rest, then reinstall your operating system (as long as you have really good backups. I really don't want to see you in the Absolute Beginner forum posting "Help! I lost years of data!") 

It also seems like you could benefit from some basic security knowledge.  Have a look at the wiki in my signature, then check out the security stickies in this forum. It might help to read that stuff before you decide to reinstall anything.

---

### Post by sammiev on 2012-02-27
I would think if he deleted the java folder and the browser folder and reinstalled all would be good to go again. :)

---

### Post by helpme222 on 2012-02-27
> I would think if he deleted the java folder and the browser folder and reinstalled all would be good to go again. 
I already ran bleachbit. But how do I do what you recommend?

---

### Post by helpme222 on 2012-02-28
Okay, one final question (and then I will stop annoying you people (I promise)). Was that site even infected at all? Because once I look at the sucuri log again it said "Site with issues" not "Site infected with malware".

---

### Post by OpSecShellshock on 2012-02-28
> **helpme222 said:**
> Okay, one final question (and then I will stop annoying you people (I promise)). Was that site even infected at all? Because once I look at the sucuri log again it said "Site with issues" not "Site infected with malware".

Ah, well if the report has changed, and looking at the Sucuri links where it's talking about the 403 response codes, it is possible that it had something bad on it at first, but eventually those scripts or pages were removed, while the links to them remained. I still wouldn't worry just because if anything did run it would still target Windows. You have said that you ran Bleachbit, which if every box under Chrome was checked would have gotten rid of anything left behind from the session. Still think you're OK.

---

### Post by helpme222 on 2012-02-28
> **OpSecShellshock said:**
> Ah, well if the report has changed, and looking at the Sucuri links where it's talking about the 403 response codes, it is possible that it had something bad on it at first, but eventually those scripts or pages were removed, while the links to them remained. I still wouldn't worry just because if anything did run it would still target Windows. You have said that you ran Bleachbit, which if every box under Chrome was checked would have gotten rid of anything left behind from the session. Still think you're OK.
Okay, thanks. :)

---

