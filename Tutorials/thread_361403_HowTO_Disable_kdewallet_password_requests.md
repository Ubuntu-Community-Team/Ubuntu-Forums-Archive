---
title: "HowTO: Disable kdewallet password requests"
date: 2007-02-14
forum: Tutorials
---

### Post by Old Pink on 2007-02-14
When using KDE applications which require password access (such as Kopete or kftp) kdewallet often offers to remember the password in a wallet in exchange for you entering a singular password each time you open that application. 

Often, some GNOME users will experience this too, as the majority of KDE applications will run on GNOME with the bare KDE essentials. Often these applications will download kdewallet as a dependency should it be accquired from the repositories. 

Anyway, it's very easy to stop this little popup each time you open a KDE application, simply follow these steps:
[LIST=1]
[*]Run "kdewalletmanager" from terminal or Alt + F2
[*]Open the configuration dialogue (Settings > Configure), and uncheck "Enable the KDE Wallet subsystem"
[*]Close the two open dialouges, and try your favorite KDE application.[/LIST]Sorted! Should've worked instantly. 

*Note: I understand this is fairly trivial information, but newbies ask this question often, and it's good to have a HowTO available with a quick search. :KS*

---

### Post by hendo on 2007-02-18
I'm a newbie to all this, and i hope you don't mind me correcting you, but on my system (GNOME 6.06 Dapper) the commands are slightly different.

Opening the wallet manager requires the command "kwalletmanager", not "kdewalletmanager".

Also, when the wallet opens, there's a good chance that it will only open as a small icon in the system tray/toolbar. It took me a few minutes to find the icon and click on it to get the Wallet Manager window to display on the desktop.

Finally, under the "Settings" menu, you need to select "Configure Wallet".

---

### Post by fede on 2007-02-20
Thanks!

---

### Post by texas.chef94 on 2008-08-22
I am running ubuntu 8.04 with a kbuntu desk top (hope that phraseology is correct. I tried kdewalletmanager as well as alt+f2 and neither recognized the command or file name.
Allen

---

### Post by cefn on 2010-01-19
These instructions were very troublesome to me on a Gnome-based desktop. So much so that I would not recommend following them. Indeed you may prefer to remove Choqok in favour of a better integrated Twitter client.

My experience was as follows...

kdewalletmanager indeed did not exist, and to follow these instructions (to remove password prompts) I had to install kwalletmanager...

sudo apt-get install kwalletmanager

...I then launched the kwalletmanager, which appeared in the system tray. I launched the preferences window by clicking on the icon - right or left, I don't remember, and I don't want to repeat the test. 

After unchecking the checkbox in order to disable the kde wallet my desktop became filled with hundreds of duplicate error windows trying to tell me there was a problem. The only way to recover my system was to very quickly launch a terminal and run

killall kwalletmanager 

This kind of quality issue is really unacceptable in a package provided as part of a Gnome distribution, and unless the KDE developers create packages which have properly configured dependencies and play nicely then there will remain a chasm between the two.

---

### Post by menkhaf on 2010-02-12
> **cefn said:**
> After unchecking the checkbox in order to disable the kde wallet my desktop became filled with hundreds of duplicate error windows trying to tell me there was a problem. The only way to recover my system was to very quickly launch a terminal and run

killall kwalletmanager 

This kind of quality issue is really unacceptable in a package provided as part of a Gnome distribution, and unless the KDE developers create packages which have properly configured dependencies and play nicely then there will remain a chasm between the two.
I can confirm the massive amount of error messages when disabling the kwallet subsystem. I had a terminal open, and the windows spawned too fast to render themselves completely.

---

### Post by shayli147 on 2011-02-05
hello:)
the kdewalletmanager didn't exist for me as well yet kwalletmanager did. i followed the instruction that appeared to me in the terminal and installed it. afterwards i tried to type kwalletmanager once again and this is what i got:
> Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)

i seriously have no idea what that means, but nothing opened, not even a small icon in the system tray as opened to hendo.
what should i do next?

[sorry if this isn't the right place]

---

### Post by H4rm0ny on 2011-05-10
I had the same problem with KDEsvn which triggers a request to open the wallet about every 8 seconds. As you can imagine - not a problem I intend to put up with for very long.

On 11.04 there appears to be no way to access KWalletManager. You can install it and you can run it, but it just sits there in the background list with no way of being accessible from the Gnome desktop.

The workaround that I found is to edit the KDE Wallet config file directly. Then you don't have to faff around with finding non-existent icons.

Go to **~/.kde/share/config**

Edit the file **kwalletrc**

Set the line **Enabled=True** to **Enabled=False**.

Note you may be tempted to set the line to **Enabled=FalseAndNeverRunThisBloodyProgramAgain** but False is sufficient.

Hope this helps people. The wisest thing to do when installing KDE apps on Gnome is the moment that first request asking you if you'd like to use Wallet appears, is to click 'No' very hard.

Harmony.

---

### Post by oldmankit on 2011-06-28
I'm through trying to find something that works as nicely as tweetdeck used to for me.  I thought choqok was the one, and then this crappy password issue for gnome users.  Farewell, bade me good luck on my twitter travels in the world of closed source air.

---

### Post by geazzy on 2011-06-30
nice threads :)

---

### Post by JoeNinety on 2011-11-03
> **H4rm0ny said:**
> The workaround that I found is to edit the KDE Wallet config file directly. Then you don't have to faff around with finding non-existent icons.

Go to **~/.kde/share/config**

Edit the file **kwalletrc**

Set the line **Enabled=True** to **Enabled=False**.

Note you may be tempted to set the line to **Enabled=FalseAndNeverRunThisBloodyProgramAgain** but False is sufficient.

Hope this helps people. The wisest thing to do when installing KDE apps on Gnome is the moment that first request asking you if you'd like to use Wallet appears, is to click 'No' very hard.

Harmony.

This worked for me. Using kmail on linux mint 11.04, which uses Gnome as the desktop. When installing kmail I was asked if I wanted to use kwallet and agreed. kmail would (almost) freeze periodically and I noticed that the kwallet daemon appeared in the hung process list when I had to shut the system down. Now kmail does not ask for the kwallet password.

---

### Post by DreamcasterTM on 2012-04-18
Something wrong with following your instructions on Ubuntu 11.04 and Unity.
kdewalletmanager was already installed (!), but it did not run when I tried to click on the icon.
From terminal: sudo apt-get install kwalletmanager
It installed. kdewalletmanager disappeared and kwalletmanager (wit a nicer looking icon) took its place.

unfortunately, not even this one seems to run (no icons in the system tray).

kopete still asks me to input my master passwords everytime i run it.

---

