---
title: "disabling GTK's 'middle mouse paste' functionality"
date: 2011-09-17
forum: Tutorials
---

### Post by bughunter2 on 2011-09-17
A while ago, I wrote a patch to disable the 'middle mouse button paste' functionality in GTK. I thought that there would be others who want to disable it as well, and hence I thought I should write a small guide to explain how this feat can be accomplished.

Now, some may ask, why would anyone want to disable it? There are a few reasons:

[LIST]
[*]The middle mouse button doesn't actually paste the so called XA_CLIPBOARD clipboard, but the XA_PRIMARY clipboard. This is probably counterintuitive to many (users coming from Windows, perhaps), and therefore some may view it as more user-friendly to disable the "inconsistent" or unexpected behavior.
[*]Some may accidentally paste text using the middle mouse button, and want to avoid that.
[/LIST]
 
A bit of background regarding the XA_CLIPBOARD and XA_PRIMARY clipboard:
The XA_PRIMARY clipboard is used mostly for storing selections. Whenever you select some text in for example the GNOME Text Editor (gedit), this text is copied to the
XA_PRIMARY clipboard. This text is _not_ pasted when you use the 'Edit -> Paste' menu item, only when you click the middle mouse button. The XA_CLIPBOARD clipboard is
mostly used when one uses the general 'Copy/Paste' functionality (through keyboard shortcuts, such as CTRL+C and CTRL+V, or through the menu items 'Edit -> Copy' and 'Edit
-> Paste').

Perhaps a patch of this sort (or more drastic changes to the X clipboard and/or how libraries/applications use it) could some day become standard in Linux. Some may agree, and some may not. However, for people who seek to minimize the chances of accidentally pasting some random text, the patch can be pretty useful. For example, with the patch, you can't accidentally paste (at least, with the middle mouse button) text into a document you are editing, or into a web page, or into an instant message, etc.

Anyway, enough, onto the guide.

What follows are terminal commands with a brief description of what they do (the lines starting with # are comments, which contain these descriptions). You should start a
terminal and enter the commands one by one, after carefully reading the descriptions.

```
# This is a small guide that explains how to patch GTK so that the middle mouse
# button doesn't paste text anymore.

# NOTE:
# The below instructions are for GTK2. However, they should be easy to adapt
# for GTK3 (at the time of writing, the patch works fine for GTK3 too).

# First, update the system by first synchronizing the package index files, and
# then upgrading the packages.
sudo apt-get update
sudo apt-get upgrade

# Get the build dependencies and essential packages needed in order to compile
# code and create packages.
sudo apt-get build-dep libgtk2.0-0
sudo apt-get install build-essential

# Create a temporary directory, in which we will store the GTK sources and
# later on the packages.
mkdir /tmp/gtk
cd /tmp/gtk

# Download the actual patch that will disable the 'middle mouse button paste'
# functionality (it should be stored in the directory '/tmp/gtk', and will be,
# if you indeed executed the command 'cd /tmp/gtk').
wget http://subversion.assembla.com/svn/slipstream/patches/gtk_disable_middle_mouse_button_paste.patch

# Retrieve the GTK sources.
apt-get source libgtk2.0-0

# You should adapt this line so that it changes to the correct directory (the
# name of the directory that I used here will probably not match the name of
# the directory that was created during 'apt-get source libgtk2.0-0', as it
# contains a version number that often changes). You can find out what the
# correct directory is by entering 'ls -d */' (without the quotes) and looking
# at the names of the directories that it shows.
cd gtk+2.0-2.20.1

# Apply the patch that we downloaded earlier.
patch -p1 < /tmp/gtk/gtk_disable_middle_mouse_button_paste.patch

# The output of the previous command should be:
#     patching file gtk/gtkselection.c
# If it wasn't, then something went wrong. Maybe you mistyped something, maybe
# the current directory isn't the correct directory, maybe the GTK sources
# so that the patch doesn't anymore apply, etc.

# Build the package (you may have to be patient, this may or may not take a
# while).
dpkg-buildpackage -uc -us

# You should adapt this line so that it installs the correct package. The
# package that we want to install is the package containing the GTK library,
# thus _not_ the 'bin', 'udeb', 'common', 'dev', or 'doc' package. To find out
# what the exact package is that you should install, try to find the package (a
# file with a name ending in '.deb') which is closest to the example filename I
# used here (the packages are stored in '/tmp/gtk', and you can list the
# packages using the command 'ls /tmp/gtk/*.deb' (without the quotes)).
sudo dpkg -i ../libgtk2.0-0_2.20.1-2_i386.deb

# And lastly, to make sure that only the patched library is in use, you should
# either log out and back in, or restart your computer.
# And then, the 'middle mouse button paste' functionality should be disabled.
# To test whether it is, try selecting some text in the GNOME Text Editor, or
# in a GNOME Terminal, and then press the middle mouse button while the cursor
# hovers over some place where you can normally type text. If indeed no text
# appears, then it appears that the patch worked.
# If however, the patch did not work, try to re-read this document, to see if
# you made any mistake. And if you did, you may want to either start all over
# again (should be fail-safe), or continue with the guide from the point where
# you made a mistake.

```

---

### Post by wernerml on 2013-04-19
> Why it isn't working in Debian Wheezy (KDE)?
I have tryied EVERY POSIBILITY in the universe... compiled/builded/re-compiled/re-builded millions/billions of times...
I don't understand... GTK seems to have nothing to do with the Debian/KDE/X clipboard....
need help!

EDIT: WOW, I FOUND IT:

[http://unix.stackexchange.com/questions/24765/disable-modify-middle-click-to-paste-in-x11-xorg](http://unix.stackexchange.com/questions/24765/disable-modify-middle-click-to-paste-in-x11-xorg)

I need to recompile QT also...

---

