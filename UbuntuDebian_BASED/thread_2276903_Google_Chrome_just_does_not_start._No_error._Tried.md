---
title: "Google Chrome just does not start. No error. Tried reinstalling and nothing"
date: 2015-05-05
forum: Ubuntu/Debian BASED
---

### Post by altjx on 2015-05-05
I'm at a stand still here. For some reason after running updates, Google Chrome stopped working. This happened about two weeks ago, but I've never really cared until now.

When I run google-chrome from the CLI, nothing happens. It hangs as if it's launching, but it never loads. Here's what it looks like:

```
root@ubuntu:# google-chrome-stable 


```

The cursor just sits on the blank line as if it's running. There's never any error messages. I've tried uninstalling and re-installing Google Chrome from the repositories. Also tried downloading it directly from Google's website. Also cleared out ~/.config/google-chrome/ just to be on the safe side. Any other suggestions?

---

### Post by RobGoss on 2015-05-05
Are you trying to install it for your terminal? if so you're terminal commands are not correct

It should be,

```
 sudo apt-get install google-chrome-stable
```

You should be able to install it for the Ubuntu software center also

---

### Post by altjx on 2015-05-05
> **robert159 said:**
> Are you trying to install it for your terminal? if so you're terminal commands are not correct

It should be,

```
 sudo apt-get install google-chrome-stable
```

You should be able to install it for the Ubuntu software center also

I'm not trying to install it. I'm trying to **start** it. It's installed already apparently, but it just won't open.

Thanks for your feedback.

---

### Post by roger_1960 on 2015-05-05
Hi

Why are you trying to run it as root?  Not normal in ubuntu.  Was it installed in the root user folder?

Do you recall what the updates were which seemed to cause it to stop working?

Roger

---

### Post by RobGoss on 2015-05-05
What version of Ubuntu are you currently running?

Like Roger stated it might be one of the updates you install that is causing this problem.

---

### Post by altjx on 2015-05-05
> **roger_1960 said:**
> Hi

Why are you trying to run it as root?  Not normal in ubuntu.  Was it installed in the root user folder?

Do you recall what the updates were which seemed to cause it to stop working?

Roger

Eh, well I'm actually running it in kali. And I've usually just been able to append a parameter towards the end to get it to work under root. It was installed as root from the get go as well. I know I'm not in the right forum, but figured I'd try any solutions anyway that were thrown at me since the community is usually fast with responses.

Not quite sure about the specific update. It's a bit long overdue since I should have came here.

---

### Post by RobGoss on 2015-05-05
I just came accross this post it might help with your problem [http://ubuntuforums.org/showthread.php?t=1346956&page=2](http://ubuntuforums.org/showthread.php?t=1346956&page=2)

---

### Post by altjx on 2015-05-05
> **robert159 said:**
> I just came accross this post it might help with your problem [http://ubuntuforums.org/showthread.php?t=1346956&page=2](http://ubuntuforums.org/showthread.php?t=1346956&page=2)

Thanks for pointing me to the link. I've verified that all of the files/folders referenced in that thread are owned by the root user, and that's the only user I've been logged in as on this system since the initial install.

---

### Post by roger_1960 on 2015-05-05
Hi again

To be honest, I know nothing about kali (that can't be googled) so I don't think I can help

Roger

---

### Post by altjx on 2015-05-05
> **roger_1960 said:**
> Hi again

To be honest, I know nothing about kali (that can't be googled) so I don't think I can help

Roger

No problem. Thanks for your help for sure!

---

### Post by RobGoss on 2015-05-05
Question? is this a new installation of [COLOR=#000000]kali? the reasion I'm asking is maybe you can do a fresh install and it may fix your problem just my to cents.[/COLOR]

I use Ubuntu 14.10 and never had this problem with Chrome as it is my default browser but if I find out anything that may help you I will surely post it in this thread.

---

### Post by altjx on 2015-05-05
> **robert159 said:**
> Question? is this a new installation of [COLOR=#000000]kali? the reasion I'm asking is maybe you can do a fresh install and it may fix your problem just my to cents.[/COLOR]

I use Ubuntu 14.10 and never had this problem with Chrome as it is my default browser but if I find out anything that may help you I will surely post it in this thread.

Hmm, I've had this kali instance for about a year now, and I've been doing regular upgrades about once or twice a week. I'll most likely end up using a new image if I can't get this working.

Thanks again! :)

---

### Post by RobGoss on 2015-05-05
Yes I can understand your frustration when something like this happens I would not want to start from scratch my self. It seems like you did all you can to resolve this by reinstalling Chrome.

---

### Post by oldos2er on 2015-05-05
Moved to Other OS Support and Projects.

---

