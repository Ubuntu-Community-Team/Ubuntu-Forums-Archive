---
title: "gnome-keyring ssh agent timeout"
date: 2009-09-21
forum: Security
---

### Post by Mr_Toph on 2009-09-21
Took me quite a bit of hunting to find all this info, so thought I'd post it all in one easy place. :)

Under a default Ubuntu 9.04 install, when you have an SSH key under one of the default names (id_rsa, id_dsa, id_rsa_gnome..) the seahorse/gnome-keyring agent will identify it, and load it automatically. You'll get a little prompt asking for the passphrase, and then you'll log in. However, the agent caches key, and you will not be prompted again for the duration of your login.

Some people may like this, but it also comes at a slight security risk. You can choose to disable this functionality with the following command:
```
gconftool-2 --set -t bool /apps/gnome-keyring/daemon-components/ssh false
```

However, SSH agents are helpful sometimes. If you need to move quickly between servers, it can get repetitive to type in your passphrase over and over again. One option is to set a "key timeout". This allows it to cache the key in the agent for a certain amount of time, and then it is purged out. Kind of a happy medium between entering your passphrase every time, and having it cached for your whole session. Normally, this would be done with "ssh-add -t <secs>" if you were using the command line agent. However, there is no currently no option to do this with the graphical gnome-keyring.

It appears that this "bug" has been identified and is being worked on (Ref: Gnome BugZilla #[525574]("https://bugzilla.gnome.org/show_bug.cgi?id=525574")).

However, I needed a solution in the meantime. What I came up with, was a script that monitors the dbus to identify when the gnome screensaver activates, and when it does, purge the cached keys from the ssh agent with a "ssh-add -D".

First you need to create a script and dump the following into it.
```
#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
if (m/^\s+boolean true/) {
system("ssh-add -D");
}
}
```
(Credit to [Streeterer]("http://ubuntuforums.org/member.php?u=702610") for the original version of this script, [here]("http://ubuntuforums.org/showthread.php?t=1029704").)

Then you'll need to set this script to run at login. You do this by going to System>Preferences>Sessions, and create a new session object for "/usr/bin/perl <path-to-the-script>".

Voila! When your Gnome Screensaver activates, the script will run "ssh-add -D", which will tell the seahorse/gnome-keyring daemon to purge all cached SSH keys from it's memory.

---

