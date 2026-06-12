---
title: "Blocking executables for individual users"
date: 2009-10-13
forum: Security
---

### Post by kelvinator on 2009-10-13
I permit my daughter (aged 6+) to use my PC from her own account.
Today I noticed that she downloaded some windows executables in an apparent attempt to install games. Is there a way to configure firestarter on a user-by-user basis to block downloads? If not what firewall software can I use that would do this?

---

### Post by rookcifer on 2009-10-13
Are you only worried about Windows executables or do you want to prevent her from downloading any file whatsoever?  (BTW, Windows executables cannot run on Linux unless WINE is installed, so no worries there).  If you are only worried about security, then I don't think you have too much to worry about as long as she doesn't know the root password.

At any rate, a lot of the answer to your question is going to depend on your daughter's level of expertise with Linux.

---

### Post by kelvinator on 2009-10-13
> **rookcifer said:**
> Are you only worried about Windows executables or do you want to prevent her from downloading any file whatsoever?  (BTW, Windows executables cannot run on Linux unless WINE is installed, so no worries there).  If you are only worried about security, then I don't think you have too much to worry about as long as she doesn't know the root password.

At any rate, a lot of the answer to your question is going to depend on your daughter's level of expertise with Linux.

Her knowledge of linux is very limited - she knows how to fire up the web browser. HOWEVER I'd rather not have her downloading any files without me being beside her. The machine does have WINE installed.

---

### Post by shaggy999 on 2009-10-14
I think that would be very hard to do. Everything that a web browser obtains is a file, whether it be a webpage, a picture embedded in a webpage, script files that run on that page, etc. I don't think there's a way to say "don't download files" because the firewall can't tell if a file is needed for a web page or if it's something being permanently downloaded. That's all transparent to the firewall, you would want to look at the browser itself. There might be a plugin for firefox, but I doubt it.

Are there specific types of files you want to ban? That would be a lot easier. For example, not allowing the transfer of .exe files.

But really, what does it matter what she downloads? She can't harm the system in any way. If you're wanting to block certain content (pornography) there are plugins for that.

Perhaps you should just restrict the firefox binary so that it can only be run by you so you would need to be there for her to even start firefox.

You have to remember there are other vectors as well. If you ban a file from being transferred over http there's no reason why she couldn't log onto pidgin and have the file transferred through the chat program, which uses a different protocol.

---

### Post by shaggy999 on 2009-10-14
You might want to look into this:

[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

---

### Post by Lars Noodén on 2009-10-14
KDE and Xfce have kiosk modes which can be of use.

At the other end of the complexity spectrum would be systrace or selinux.  

If the /home directory is in its own partition, then you can have that partition mounted noexec and nothing there can run.   Be sure to also do the same for /tmp and /var/tmp.  If you don't want those in separate partitions, you can make directories in /home for them and then symlink from /.

---

