---
title: "installing additional languages (HR=croatian)"
date: 2005-04-17
forum: Repositories &amp; Backports
---

### Post by Birdy27 on 2005-04-17
Hi,

I'm new to Ubuntu. I've chosen ubuntu as the solution for the following problem:
I have a friend who got his first computer, he mainly speaks croatian, while I mainly speak german or english. 

To support him with his computer I wanted to install ubuntu for him (installing in german) and then after the installation installing croatian (HR) language and setting that to default for him. (And the system should fall back to german where croatian is unavailable (he doesn't speak a word english.)

I have only found a language and a base üpackage for croatian (I expected most applications (firefox,gimp,Openoffice) to have seperate croation packages) and I installed those packages.

Sadly switching to croatian won't work "hr_HR.UTF-8 is missing falling back to german" is the message after the login.

How can I solve this problem.
How can I make sure that all programs fo which coratian exists have their language packages installed.
What is the best/most complete way to add a language to Ubuntu?

Thanks for your help!
And thanks for Ubuntu!

Greetings
 Christoph

---

### Post by erkki70 on 2005-04-17
Hi,
Try this command:
 ```
sudo dpkg-reconfigure locales
```
enter your password and then select the languages from list.
From the login window Click on language and then select Croatian from the list as your default language or session language to run Ubuntu with all menus translated to Croatian. Extra packages for Firefox and OOo I guess you have them already installed from Synaptic. ;-)

Hope this helps.

Cheers,
Erkki

---

### Post by Birdy27 on 2005-04-17
Thank you!

That solved the problem :-)
As well as it raised a new one (see next post)

---

### Post by Birdy27 on 2005-04-17
Now I have a partially croatian Menu, but where ever there is no croatian translatian it uses english.

Can I some how set it up in a way that it uses croatian, if something is not available it uses german (system default) and only if nothing else is possible it uses english?

Thanks!

---

### Post by erkki70 on 2005-04-17
Hi,
Have a look here to get a clearer picture about Gnome translated in Croatian:
[http://l10n-status.gnome.org/gnome-2.10/hr/desktop/index.html]("http://l10n-status.gnome.org/HEAD/hr/index.html")
So yep, unfortunately you're missing still quite much...

Now, changing the English strings to German.... Wow! 
Sorry, no idea... Manually modifiying the .po translation files if you're up to.
All the strings are translated from English like this,  ```
 msgid "<b>Options</b>"
msgstr "<b>Optionen</b>" 
``` 
though I believe (not sure about that, but logic) msgid has to be in English so... it might be just not possible. Or then mix the DE and HR po translation files to change the strings only...
Don't think anyone has ever done that...
 Well, a very good thing you could do is starting to contribute to help translating to Croatian... 

Good luck.

Cheers,
Erkki

---

