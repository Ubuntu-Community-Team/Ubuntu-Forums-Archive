---
title: "How To Install a Cool Additional Update Tool in Ubuntu"
date: 2019-11-12
forum: Tutorials
---

### Post by computertip on 2019-11-12
It's possible to supplement the rather basic update tool of Ubuntu, with a more advanced tool called Update Manager. Made by a former developer of the Update Manager of Linux Mint, so of high quality and reliable.

This advanced tool will give you much more control over your updates! It'll also give you some useful fine-grained control over your Linux kernels.

The how-to below, is an abbreviated version of [the how-to on the Easy Linux Tips Project]("https://easylinuxtipsproject.blogspot.com/p/ubuntuplus.html").

**Note (1):** This tool has been designed for, and tested on, main edition Ubuntu. I have only done limited testing on other official Ubuntu flavours like Xubuntu, Ubuntu MATE et cetera. But it should work fine in those as well.

**Note (2):** This how-to isn't meant for Linux Mint. Mainly because Linux Mint already contains a rather similar tool by default.

**Note (3):** Although Update Manager has been forked off the official Linux Mint Update Manager, it's not exactly the same as that anymore. After his retirement from the official Mint developers team, its developer has modified "his" Update Manager in certain respects.

This is what to expect (just a highlight of some of its features):

[SIZE=4]**Update Manager: take full control of your updates and your kernels**[/SIZE]
1. Update Manager can be configured to show a permanent icon in the system bar, indicating whether there are any available updates or not. When there are no updates, it's a green check in a white shield:

[IMG]https://1.bp.blogspot.com/-SrRzqNNkjGc/XcAIA6qoJeI/AAAAAAAABTA/exsEowLqfIQdwDW5CYwUtATWfj0k_o7pACLcBGAsYHQ/s1600/Screenshot-gm10-1.png[/IMG]

When there are updates, it becomes a white exclamation mark in a blue shield:

[IMG]https://1.bp.blogspot.com/-IQcaSrFEdFw/XcAIQE3KYiI/AAAAAAAABTE/Anwm_TJ350YWH6J2yutUqkCM-bFd1n4OACLcBGAsYHQ/s1600/Screenshot-gm10-2.png[/IMG]

The only other notification you get of available updates, is a desktop notification that remains in sight for a few seconds. So it's very unobtrusive, unlike Ubuntu's Update Notifier....

This is its main window:

[IMG]https://1.bp.blogspot.com/-p9Svxu1zMbk/XcBkGpo8S4I/AAAAAAAABUg/zA1hQasdrlIbo5G8Wre4Eg4r10Jsv2S9ACLcBGAsYHQ/s1600/Screenshot-gm10-20.png[/IMG]

When you click Tools - Linux Kernels in the panel of Update Manager, you launch a nifty kernel tool. This gives you advanced control over the kernels. With this, it's for instance very easy to install another kernel.

When you click the button ***Remove Kernels...***, you can remove all superfluous kernels in one stroke, by means of the next dialogue window you get to see:

[IMG]https://1.bp.blogspot.com/-WQRnPFJ3wVA/XcALAPYAy5I/AAAAAAAABTw/IjYpO1ddDAQ9p2VoXiZyF4erLWUx39q6ACLcBGAsYHQ/s1600/Screenshot-gm10-6.png[/IMG]

When you click Edit - Preferences: tab Automation in the panel of Update Manager, you can automate the removal of all superfluous kernels (barring the latest superfluous kernel, which acts as reserve, and also barring any manually installed kernels).

It's also very easy to blacklist an update, either just the current version of that particular update, or all future updates for a particular package. All it takes is a right-click on an update:

[IMG]https://1.bp.blogspot.com/-IUGhXp5ezQ4/XchdX3KwspI/AAAAAAAABXc/6W1YrYuB5UgbcGb6VouiFN_zMnZn1O6NACLcBGAsYHQ/s1600/Screenshot-gm10-30.png[/IMG]


If you wish to edit the blacklist, that's easy as well (panel of Update Manager: Edit - Preferences: tab Blacklist).

An example of a situation when this advanced blacklist feature can be very handy: suppose you know that a particular kernel update is troublesome, so you wish to avoid it. But you do want to be notified about its future successor.

In that case you can simply right-click that kernel update in Update Manager and select **Ignore the current update for this package**.

Finally, when you click Tools - History of Updates in the panel of Update Manager, you can see all information about past updates. That can be useful for troubleshooting purposes.

[SIZE=4]** Timeshift: easy system restore**[/SIZE]
2. I advise to install a third-party tool called Timeshift as well, which is being made by another developer. Although Update Manager can also function without Timeshift, a couple of its features have been tied rather closely to it.

With Timeshift you can create snapshots of your system, in order to be able to roll back your system to a working state after it has been damaged. You can compare those snapshots with system restore points in Windows.

[SIZE=4]**How-to for Ubuntu 18.04**[/SIZE]
3. OK, enough talk. Let's get started with this fine software:

a. Launch a terminal window.

b. Now you're going to add the Update Manager PPA to your sources list. You have to make a choice, because there's a stable frozen source that's only being updated very rarely, and an also stable dynamic source that gets new versions nearly every week.

When in doubt, I advise to select the frozen source; that has the lowest risk of breakage. Breakage in the dynamic source usually gets fixed very quickly, by the way, so breakage is not a very big deal. But still.

OK, make your choice:

***Option 1: the frozen source (recommended)***

Use copy/paste to transfer the following command line into the terminal:

```
sudo add-apt-repository -y ppa:computertip/mint-tools-ubuntu
```

Press Enter. Type your password when prompted; your password will remain entirely invisible, not even dots will show when you type it, that's normal.

Continue with step c.

***Option 2: the dynamic source***

Use copy/paste to transfer the following command line into the terminal:

```
sudo add-apt-repository -y ppa:gm10/linuxmint-tools
```

Press Enter. Type your password when prompted; your password will remain entirely invisible, not even dots will show when you type it, that's normal.

c. Then add the Timeshift PPA to your sources list, with this terminal command:
```
sudo add-apt-repository -y ppa:teejee2008/ppa
```

d. Install the necessary supporting (Mint) files with the following terminal command:
```
sudo apt-get install mint-common
```

e. Now install both Update Manager and Timeshift, with this terminal command:
```
sudo apt-get install mintupdate timeshift
```

f. Then you need to restrict the old Ubuntu update tool, in order to make full way for the new tool. It's namely better not to use both the old and the new tool.

First disable the automatic start of Ubuntu's Update Notifier. In a way that's easy to reverse, in case you'd ever want to undo all this. That can be done with the following two terminal commands, with which you move the automatic launcher file of Update Notifier to a dedicated "parking lot":

To begin with, you create the parking folder:
```
sudo mkdir -v /parking
```

Then you move the file to its parking lot with this command line:
```
sudo mv -v /etc/xdg/autostart/update-notifier.desktop /parking
```

g. Then you launch the application Software & Updates. Click on the tab **Updates** and set **Automatically check for updates:** to **Never**. With that, you've adequately restricted the Ubuntu update tools.

h. Reboot your computer.

i. Configure your new Update Manager to show a permanent icon in the desktop panel. Launch Update Manager - panel: Edit - Preferences
Enable the following option:
**Use AppIndicator for the tray icon (more limited but supports more desktops)**

j. Timeshift is a nifty tool, but it definitely needs some restraints on its potential disk usage. So restrict the number of kept snapshots to 2, and in case of scheduled ***automatic*** snapshot taking: restrict it to monthly with a retention of 2. Nobody needs more than that.

k. Enjoy!

[SIZE=4]**How to undo**[/SIZE]
4. Regrets? Unlikely to have those, but you can undo all this as follows:

a. Remove the two installed applications and their supporting package, with this terminal command:

```
sudo apt-get remove mintupdate timeshift mint-common
```

b. Move the starter for Ubuntu's Update Notifier back to its old spot, with the following command:

```
sudo mv -v /parking/update-notifier.desktop /etc/xdg/autostart
```

c. Launch the application Software & Updates, go to its tab **Other Software** and remove the PPA's from **teejee2008** and **computertip** or **gm10** from your sources list.

d. Still in Software & Updates, click on the tab **Updates** and set **Automatically check for updates:** to **Daily**.

e. Reboot your computer. All should be as it was before.

---

### Post by computertip on 2019-11-14
I've created a PPA with a frozen version of the Mint tools for Ubuntu. For those who prefer a frozen PPA that gets updates very rarely, over a dynamic PPA that gets updates nearly weekly. The choice is yours....

I've modified the how-to accordingly.

---

