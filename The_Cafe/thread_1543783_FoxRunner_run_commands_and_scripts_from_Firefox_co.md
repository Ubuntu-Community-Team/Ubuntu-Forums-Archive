---
title: "FoxRunner: run commands and scripts from Firefox context menu, sidebar and statusbar"
date: 2010-08-01
forum: The Cafe
---

### Post by lovinglinux on 2010-08-01
I have released version 1.0.6 of [FoxRunner]("http://www.webgapps.org/addons/foxrunner"), an extension for Firefox that makes the process of running commands from web sites a lot easier.

With [FoxRunner](http://www.webgapps.org/addons/foxrunner) you can run shell commands from any web page through the context menu. Just select a command from a forum post or web article and run it. You can also save commands and scripts, then launch them through Firefox sidebar, context menu and status bar. 

[Blog]("http://www.webgapps.org/addons/foxrunner") | [Mozilla]("https://addons.mozilla.org/en-US/firefox/addon/98430/")

**[COLOR="Sienna"]ToDo[/COLOR]**

[LIST]
[*]provide support for web site commands with multiple lines
[/LIST]

**[COLOR="Sienna"]Security Notes[/COLOR]**

Although Firefox extension API does not allow unprivileged content to access extensions functions, which means a web site cannot execute a malicious terminal command through FoxRunner, I have included several security measures that allow the user to have full control on how and what is executed. These measures were included, mostly to prevent the accidental execution of dangerous commands. Nevertheless, if you enable all security options, you won&#8217;t be able to execute a command from the context menu, while visiting a web site that is not included in the allowed list or a command that is blacklisted. Additionally, there are distinct options to control how a command from the database or from text selected form a web site is managed. So you can for example be more conservative with commands from sites, while allowing commands from the database to run without confirmation. This security model received a very positive review by the Mozilla editor who approved FoxRunner, as quoted below:

> **I liked very much how seriously you took the security of your add-on users. Keep up the good work!**

*[Jorge Villalobos](https://forums.addons.mozilla.org/memberlist.php?mode=viewprofile&u=4230) -- Mozilla&#8217;s Add-on Developer Relations Lead*


[IMG]http://lh3.ggpht.com/_EPRFmO0pKhs/S-VzNMyVAqI/AAAAAAAAAGs/GDmIFcpZN5E/s288/foxrunner_002.png[/IMG]

---

### Post by simonbcn on 2010-10-15
Hi,
I'm using your extension and it's good but:
1) What's the utility of scripts with parameters if I can't write that parameters in execution time?
2) It would be great that the *statusbar command box* hides itself after it executes a command.

---

### Post by lovinglinux on 2010-10-15
> **simonbcn said:**
> 1) What's the utility of scripts with parameters if I can't write that parameters in execution time?

Good point. That is the less developed feature of FoxRunner in my opinion and I'm thinking about working on it for some time. Thanks for the suggestion.

About it's utility, it was designed with my personal repetitive tasks in mind. For instance, I use it a lot while developing my extensions. I have a list of parameters with all my extensions IDs (name) and I use it for pushing changes to repositories, creating archives for release, comparing code changes and more. Is not good tho, if the same parameters are not reused often. 

> **simonbcn said:**
> 2) It would be great that the *statusbar command box* hides itself after it executes a command.

I think it could be useful to implement that option, but making that the default behavior is not good in my opinion. The idea of that box is convenience, so the less clicks I need to get the command executed, the better.

It will take some time to implement that, since the command box is broken on Firefox 4, which doesn't have a statusbar anymore.

---

### Post by lovinglinux on 2010-11-06
FoxRunner 1.0.7 is now available for download through GitHub and will be available through the Stable Channel and Mozilla site as soon it gets reviewed by Mozilla editors. 

This version fixes (for real) the child process error that affects Firefox profile names with spaces. Additionally, the statusbar launcher has been removed due to upcoming changes in Firefox 4.

---

### Post by ambeginnersearchinginfo on 2010-11-06
Dear, Lovinglinux,

I first repeat as I understand FoxRunner. I use Ubuntu 10.10 cd as a live system.

FoxRunner is a free software like the Mozilla Firefox browser.
It can be inserted in the isoimage of Ubuntu 10.10 or later without an
license/licence problems like the Mozilla Firefox browser, if it is not allready in the Ubuntu isoimage, what I don't know. I now see the firdt time the FoxRunner mentioned in this thread.
A command which is executable  in the terminal
could be executed by clicking on its icon on a bar of the Mozilla Firefox browser window,
like a launcher on a gnome bar of ubuntu, and FoxRunner can install the icon and the launcher on the bar of the Mozilla Firefox browser window.

I want to use the following command: sudo setxkbmap -model pc105 -layout 
for various languages.

Let's say I open eight browser windows, one for each of the first eight input languages and I have on the bars of the browser windows ten icons for switching among the ten the languages.
If the browser window number one is active and its input language is language number one and if I click then on the icon of the input language number nine on the bar of this active window, could I switch the input language for this active window without effecting the other seven windows?

How many icons for switching languages I could get on the bar, is there a limit?

By which terminal command(s) I could create these launcher and put them on the bar of
  the Mozilla Firefox browser windows or by which other method I could get this into the isoimage in order to have all the desired input language switching icons automatically on the bars of all  Mozilla Firefox browser windows every time I switch on the computer to start my Ubuntu 10.10 cd live system?

Thank you very much.

---

### Post by lovinglinux on 2010-11-06
> **ambeginnersearchinginfo said:**
> FoxRunner is a free software like the Mozilla Firefox browser.
It can be inserted in the isoimage of Ubuntu 10.10 or later without an
license/licence problems like the Mozilla Firefox browser, if it is not allready in the Ubuntu isoimage, what I don't know.

It is released under GPL3, so yes. You can distribute and modify it to your liking, according to the GPL license terms.

> **ambeginnersearchinginfo said:**
> If the browser window number one is active and its input language is language number one and if I click then on the icon of the input language number nine on the bar of this active window, could I switch the input language for this active window without effecting the other seven windows?

FoxRunner is not tied to Firefox profiles in a way that you can run commands for specific Firefox windows. What it does is to store commands and allow to run them any time you want and also run commands by selecting command texts from web sites. It will use a regular terminal or will execute the commands as bash script according to your settings. So using FoxRunner to run the commands you want is not any different than copying and pasting them on a terminal. It is more convenient tho, since you can save many different versions of the same command and launch them whenever you need. 

> **ambeginnersearchinginfo said:**
> How many icons for switching languages I could get on the bar, is there a limit?

There is no limit. You can save as many commands you want, but Foxrunner does create or add any icons to your Firefox bar. It creates a database list with all commands, that you can select and click a single button to run it.

> **ambeginnersearchinginfo said:**
> By which terminal command(s) I could create these launcher and put them on the bar of
  the Mozilla Firefox browser windows or by which other method I could get this into the isoimage in order to have all the desired input language switching icons automatically on the bars of all  Mozilla Firefox browser windows every time I switch on the computer to start my Ubuntu 10.10 cd live system?

Thank you very much.

I think what you need is [Quick Locale Switcher]("https://addons.mozilla.org/en-US/firefox/addon/1333/").

---

### Post by Oxwivi on 2010-11-06
Is there a Chrome version in the making? I'd like to request it, since I'm considering a switch to Chrome, now that it's adblocking capability is nearly complete.

---

### Post by ambeginnersearchinginfo on 2010-11-06
Thank you very much for the answer.

I am not a lawyer and I am also not commercial, but I understand, that  it is a licence like linux or ubuntu and I could use it in the isoimage in order to get around the four keyboard layouts limit problem/bug in Ubuntu without facing legal licence problems.

I understand, that I could in order to get around the problem, that I don't know, how to get launchers into the isoimage in that way, that they appear automatically in the correct order on the gnome panel  as icons which show the short cuts of the languages, 
I understand, that I can save commands using FoxRunner, which I could execute like in the terminal and effect the whole ubuntu system like change the input language and also the system language, and I could execute them just by opening a Mozilla Firefox window and click on an input language icon for switching the input language and/or on an system language icon for switching the system language.
Sounds great!

And how about different icons for different languages?
And how do I get the FoxRunner with the desired settings into the isoimage in that way that the icons will appears automatically in the correct order on the bar of the Mozilla Firefox window, each time I switch on the computer and start my live system (without any persistent memory)?

Concearning the Quick local switcher, it is unclear what is about the money and the licence and does it get around the Ubuntu four language keyboard layouts problem.
If this would be the solution, then Ubuntu would have it integrated in its distribution 
and there would not be any longer a four keyboard layouts limit problem in Ubuntu,
which makes many people very very angry. so I guess somewhere is a problem that makes it not usable for that purpose.
Thank you very much.

---

### Post by lovinglinux on 2010-11-06
> **ambeginnersearchinginfo said:**
> Thank you very much for the answer.

I am not a lawyer and I am also not commercial, but I understand, that  it is a licence like linux or ubuntu and I could use it in the isoimage in order to get around the four keyboard layouts limit problem/bug in Ubuntu without facing legal licence problems.

I understand, that I could in order to get around the problem, that I don't know, how to get launchers into the isoimage in that way, that they appear automatically in the correct order on the gnome panel  as icons which show the short cuts of the languages, 
I understand, that I can save commands using FoxRunner, which I could execute like in the terminal and effect the whole ubuntu system like change the input language and also the system language, and I could execute them just by opening a Mozilla Firefox window and click on an input language icon for switching the input language and/or on an system language icon for switching the system language.
Sounds great!

And how about different icons for different languages?
And how do I get the FoxRunner with the desired settings into the isoimage in that way that the icons will appears automatically in the correct order on the bar of the Mozilla Firefox window, each time I switch on the computer and start my live system (without any persistent memory)?

Concearning the Quick local switcher, it is unclear what is about the money and the licence and does it get around the Ubuntu four language keyboard layouts problem.
If this would be the solution, then Ubuntu would have it integrated in its distribution 
and there would not be any longer a four keyboard layouts limit problem in Ubuntu,
which makes many people very very angry. so I guess somewhere is a problem that makes it not usable for that purpose.
Thank you very much.

As I said, FoxRunner does not create any icons, it just stores commands or scripts you save. For creating a personalized Live CD, see [Remastersys]("http://en.wikipedia.org/wiki/Remastersys").

---

