---
title: "Gnome-shell 3.4.0 in Precise - slight issue"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-03-27
The version 3.4.0-0ubuntu1 is now built and may be downloaded from Launchpad.
Here:
[https://launchpad.net/ubuntu/precise/+source/gnome-shell/3.4.0-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/gnome-shell/3.4.0-0ubuntu1)

Mutter 3.4.0-0ubuntu1 is also there:
[https://launchpad.net/ubuntu/precise/+source/mutter/3.4.0-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/mutter/3.4.0-0ubuntu1)

However, there is a slight issue with the new gnome-shell package.
It depends on libmutter0 <3.4 (ought to be at least <3.4.1)
This means the dependencies are not correct and after installation it leaves a kind of a broken package, due to the dependency issue.

I installed both gnome-shell and mutter 3.4 manually using dpkg.
The installation did succeed OK although for example synaptic warns about the broken package gnome-shell.
Anyways, the new gnome-shell works fine.

---

### Post by VinDSL on 2012-03-27
Interesting!

I just refreshed the repos via Synaptic, and the "Smart Upgrade" (which most ppl use by default) wanted to remove:

[LIST]
[*]Gnome-Shell
[*]Gnome-Shell-Extensions-Common
[*]Gnome-Shell-Extensions-User-Theme
[/LIST]

Hello!?!?!  :p

I think I'll suspend further updates, until this gets sorted.

---

### Post by Harry33 on 2012-03-27
> **VinDSL said:**
> Interesting!

I just refreshed the repos via Synaptic, and the "Smart Upgrade" (which most ppl use by default) wanted to remove:

[LIST]
[*]Gnome-Shell
[*]Gnome-Shell-Extensions-Common
[*]Gnome-Shell-Extensions-User-Theme
[/LIST]

Hello!?!?!  :p

I think I'll suspend further updates, until this gets sorted.

True, synaptic will not let you create dependency issues like that.
It will always remove packages instead.

If you like, you can dl those manually and install with dpkg. It works.

---

### Post by jjpdijkstra on 2012-03-27
What is the consequence of manually installing the libmutter0 that it depends on? Most likely its going to be fixed soon, so I suggest to wait until its sorted. 12.04 is going to be released with Gnome-shell 3.4 anyways. Thats where the dependency problems are coming from. Be patient.

---

### Post by dino99 on 2012-03-27
> **jjpdijkstra said:**
> What is the consequence of manually installing the libmutter0 that it depends on? Most likely its going to be fixed soon, so I suggest to wait until its sorted. 12.04 is going to be released with Gnome-shell 3.4 anyways. Thats where the dependency problems are coming from. Be patient.

Dont worry, here its the bleeding-edges fanclub :) and we are all happy when we find a way to make breakage(s) and then find a way to fix it. 
If you are afraid, maybe you have chosen the wrong subforum :)

---

### Post by flammon on 2012-03-27
A few more issues.

[LIST=1]
[*]Firefox 12 suddenly stopped working. I immediately get the Mozilla Crash Reporter.
[*]When I visit [https://extensions.gnome.org/extension/120/system-monitor/](https://extensions.gnome.org/extension/120/system-monitor/) (with chromium for now), I get the "This extension is incompatible with your version of GNOME." message which I thought was going to disappear with this upgrade.
[/LIST]

---

### Post by VinDSL on 2012-03-27
> **dino99 said:**
> Dont worry, here its the bleeding-edges fanclub :) and we are all happy when we find a way to make breakage(s) and then find a way to fix it. 
If you are afraid, maybe you have chosen the wrong subforum :)
First LOL of the day!  :D

Thanks for that, Dino.

---

### Post by Harry33 on 2012-03-27
Back to the topic.

The working version of the package gnome-shell can be downloaded from Ricotz Gnome-shell Testing PPA.
Here:
[https://launchpad.net/~ricotz/+archive/testing/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise](https://launchpad.net/~ricotz/+archive/testing/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise)

---

### Post by Harry33 on 2012-03-27
And now also in the Precise repos;
Here:
[https://launchpad.net/ubuntu/precise/+source/gnome-shell/3.4.0-0ubuntu2](https://launchpad.net/ubuntu/precise/+source/gnome-shell/3.4.0-0ubuntu2)

---

### Post by sgage on 2012-03-27
> **Harry33 said:**
> And now also in the Precise repos;
Here:
[https://launchpad.net/ubuntu/precise/+source/gnome-shell/3.4.0-0ubuntu2](https://launchpad.net/ubuntu/precise/+source/gnome-shell/3.4.0-0ubuntu2)

Just reloaded my repo data, and don't see it. Also, ricotz/testing showed it, but I couldn't install it due to dependency issues. I'm sure it will all settle out soon.

[I didn't have "proposed" enabled. I have now installed GS 3.4.0, and all seems well...]

---

### Post by PaulW2U on 2012-03-27
> **sgage said:**
> Just reloaded my repo data, and don't see it.

Downloading it now.

---

### Post by sgage on 2012-03-27
> **PaulW2U said:**
> Downloading it now.

Yeah - I'm running it now - I didn't have "proposed" enabled ):P

BTW, all you extension fans out there, if you find that your already-installed extensions don't work any more, just go to ~/.local/shared/gnome-shell/extensions. For each extension you really want to use, edit metadata.json and add "3.4.0" - you'll quickly see where to do that. There are a couple of extensions that really are incompatible, but most I've tried work just fine :KS

---

### Post by PaulW2U on 2012-03-27
> **sgage said:**
> Yeah - I'm running it now - I didn't have "proposed" enabled ):P

Have you logged out and tried to log back in again? I have, the log in seems to get stuck in and endless loop and eventually when I am able to select Gnome I log into the fallback session mode. :confused:

---

### Post by sgage on 2012-03-27
> **PaulW2U said:**
> Have you logged out and tried to log back in again? I have, the log in seems to get stuck in and endless loop and eventually when I am able to select Gnome I log into the fallback session mode. :confused:

I saw that at first, but used CTL-ALT-SysReq-K to get a clean LightDM login screen, and all was well after that. I think GS gets indigestion the first time around with extensions that are supposedly enabled but don't have the right version number. 

If you continue to have trouble, from the fallback session just move all your extensions somewhere handy. Edit the metadata.json files to add 3.4.0, and move them back as you like. It's all working fine for me now. 

I have a different bug (started in 3.3.92 actually) that I am going to look up and see if anyone else has reported it. If not, I will, and will also start a thread here.

---

### Post by PaulW2U on 2012-03-27
> **sgage said:**
> I saw that at first, but used CTL-ALT-SysReq-K to get a clean LightDM login screen, and all was well after that. I think GS gets indigestion the first time around with extensions that are supposedly enabled but don't have the right version number.

Thanks but all my extensions were deleted a few days ago. Perhaps I need to investigate.....

---

### Post by sgage on 2012-03-27
> **PaulW2U said:**
> Thanks but all my extensions were deleted a few days ago. Perhaps I need to investigate.....

I just logged out and experienced the same thing again, complete with little drumrolls every time... ctl-alt-sysrq-k brought up a clean login screen - have you tried that?

---

### Post by PaulW2U on 2012-03-27
> **sgage said:**
> I just logged out and experienced the same thing again, complete with little drumrolls every time... ctl-alt-sysrq-k brought up a clean login screen - have you tried that?

Yes, logging in works ok, log out and the problem returns.

---

### Post by sgage on 2012-03-27
> **PaulW2U said:**
> Yes, logging in works ok, log out and the problem returns.

Yes, and it does seem unrelated to extensions. Hmmm...

---

### Post by the ruler on 2012-03-28
I always get the libmutter0(>=3.4) dependency error when I want to install gnome-shell 3.4.0 in Precise.. Here's what my terminal says (in french..) :

$ sudo apt-get install gnome-shell
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation : 

Les paquets suivants contiennent des dépendances non satisfaites :
gnome-shell : Dépend: libmutter0 (>= 3.4) mais 3.3.92-0ubuntu1~12.04~ricotz0 devra être installé
E: Impossible de corriger les problèmes, des paquets défectueux sont en mode « garder en l'état ».

How do I solve this? I tried the new packages also..

---

### Post by Harry33 on 2012-03-28
> **the ruler said:**
> I always get the libmutter0(>=3.4) dependency error when I want to install gnome-shell 3.4.0 in Precise.. Here's what my terminal says (in french..) :

$ sudo apt-get install gnome-shell
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation : 

Les paquets suivants contiennent des dépendances non satisfaites :
gnome-shell : Dépend: libmutter0 (>= 3.4) mais 3.3.92-0ubuntu1~12.04~ricotz0 devra être installé
E: Impossible de corriger les problèmes, des paquets défectueux sont en mode « garder en l'état ».

How do I solve this? I tried the new packages also..

You do not have the new mutter there.
You should have the version 3.4.0-0ubuntu1 from Precise repos.
Have you enabled proposed (universe) repo yet?

Here:
[https://launchpad.net/ubuntu/precise/+source/mutter/3.4.0-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/mutter/3.4.0-0ubuntu1)

---

### Post by the ruler on 2012-03-29
> **Harry33 said:**
> You do not have the new mutter there.
You should have the version 3.4.0-0ubuntu1 from Precise repos.
Have you enabled proposed (universe) repo yet?

Here:
[https://launchpad.net/ubuntu/precise/+source/mutter/3.4.0-0ubuntu1](https://launchpad.net/ubuntu/precise/+source/mutter/3.4.0-0ubuntu1)

I couldn't install mutter 3.4 because of the same error..
But enabling all my repositories fixed it and I am running GS 3.4.0 now :)

---

### Post by VinDSL on 2012-03-29
Checked Synaptic, a few minutes ago.  Procrastination paid off again!  :D

183 upgrades were waiting, including GS & Mutter, and nothing was marked for removal.

I did the upgrades, and I am running inside GS 3.4.0 right now.

[List]Gnome-Shell: 3.4.0-0ubuntu2 (precise-proposed)

[*]Mutter: 3.4.0-0ubuntu1 (precise-proposed)
[/List]
Everything seems to be working fine!  ;)

---

