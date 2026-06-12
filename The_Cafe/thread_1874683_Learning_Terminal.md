---
title: "Learning Terminal"
date: 2011-11-03
forum: The Cafe
---

### Post by Garland Fox on 2011-11-03
Is there any easy way for this dense old dud to learn terminal use.

Or is there any hurry.

Just learn bits as I need it?

---

### Post by Legendary_Bibo on 2011-11-03
Like bash scripting? Or how to use commands?

---

### Post by Garland Fox on 2011-11-03
Thanks for reply just
meant regular commands - have no idea what bash scripting is as yet

---

### Post by irv on 2011-11-03
You might want to look at this thread:
[http://ubuntuforums.org/showthread.php?t=496911]("http://ubuntuforums.org/showthread.php?t=496911")

---

### Post by IWantFroyo on 2011-11-03
There are tasks that work a bit faster with the terminal.
Here are some of the commands I use often:
```
sudo apt-get install
```
This one installs things using the apt-get package manager (what the Software Center uses behind the scenes). You can also add --purge to completely remove any crust a package left. Using 'apt-cache search' is another function that lets you search for a package.
```
chmod +x
```
This changes file permissions. If you ever download a .sh (BASH) file that won't open, just run this on it.

After that, cd, cp, and rm (and rm -r) will get you understanding the commands you see on these forums more.

If you want to go farther, there are applications that are purely terminal apps.
- Vim is an amazing text editor. Run "vimtutor" to see how to use it.
- Alpine is a good email client.

There are plenty more at: [http://kmandla.wordpress.com/software/](http://kmandla.wordpress.com/software/)

---

### Post by Legendary_Bibo on 2011-11-03
> **Garland Fox said:**
> Thanks for reply just
meant regular commands - have no idea what bash scripting is as yet

This is a very excellent guide.

[http://vic.gedris.org/Manual-ShellIntro/1.2/ShellIntro.pdf](http://vic.gedris.org/Manual-ShellIntro/1.2/ShellIntro.pdf)

---

### Post by Garland Fox on 2011-11-03
Thanks

---

### Post by Garland Fox on 2011-11-03
Thanks a bunch

---

### Post by Telengard C64 on 2011-11-03
My Linux command line Do's-and-Don'ts:

[LIST=1]
[*]Ensure you have [*reliable* and up-to-date backups](http://blog.wisefaq.com/2010/01/05/backups-with-the-3-2-1-rule/) of any data on your system you don't want to lose forever.
[*]Never blindly enter commands you don't understand, no matter where you found them or who gave them to you. Research and ask questions first!
[*]Consider practicing on a machine which does not contain important data, or maybe a [virtual machine](http://www.virtualbox.org/). That way if you hose the system or accidentally erase the home folder you won't have lost anything but time
[*][Don't use **sudo**](https://help.ubuntu.com/community/RootSudo) unless you know you need it; if you aren't sure whether you need **sudo** then research and ask questions first. **sudo** grants any command used with it the potential to destroy all data on the system
[*]Learn to use vast quantities of documentation included with your Linux system. Your new best friends are **help command_name**, **command-name --help**, **man command-name**, and **info**.
[*]Learn to find installable documentation packages in your package manager. Not every program in *buntu is bundled with full documentation due to the limited capacity of the install media.
[*]Learn to search the web for further documentation and examples of using specific commands.
[*]Familiarize yourself with some of the best command line tutorials and references on the WWW including (but not limited to) [LinuxCommand](http://www.linuxcommand.org/), [GNU Manuals](http://www.gnu.org/manual/manual.html), [Basic UNIX commands](http://doors.stanford.edu/~sr/computing/basic-unix.html), [More UNIX Commands](http://doors.stanford.edu/~sr/computing/more-unix.html), [LINUX: Rute User’s Tutorial and Exposition by Paul Sheer](http://rute.2038bug.com/), [The Linux Users' Guide by Larry Greenfield](http://www.ibiblio.org/pub/Linux/docs/linux-doc-project/users-guide/!INDEX.html), [FTLinuxCourse by Future Technologies](http://www.ftlinuxcourse.com/), [The Linux Tutorial by James Mohr](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224), [An A-Z Index of the Bash command line for Linux.](http://ss64.com/bash/), [Bash by example, Part 1](http://www.ibm.com/developerworks/linux/library/l-bash/index.html), [Learn Linux, 101: The Linux command line](http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-1/index.html), [Learn Linux, 101: File and directory management](http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-3/index.html), [Linux Files and Command Reference](http://www.comptechdoc.org/os/linux/commands/), [Agustin's Linux manual - Volume 2 - System Administration](http://www.comptechdoc.org/os/linux/manual2/aboutauthor.html), [BashGuide BashPitfalls BashFAQ - Greg's Wiki](http://mywiki.wooledge.org/), [Bash Guide for Beginners](http://tille.garrels.be/training/bash/), [Learn UNIX in 10 minutes](http://freeengineer.org/learnUNIXin10minutes.html), [http://freeos.com/guides/lsst/index.html](http://freeos.com/guides/lsst/index.html), [GNU/Linux Tools Summary](http://www.karakas-online.de/gnu-linux-tools-summary/), [Linux.ie :: The Beginners Linux Guide](http://www.linux.ie/newusers/beginners-linux-guide/), [Linux Classes and Training.  Free Linux Lessons.](http://lowfatlinux.com/), and [Main Page - Linux Shell Scripting Tutorial - A Beginner's handbook](http://bash.cyberciti.biz/guide/Main_Page)
[*]Start small by doing simple file management tasks at the terminal instead of in your GUI file manager. Work slowly toward more complex tasks.
[*]Read and read more.
[*]Experiment, fail, and try again.
[/LIST]

HTH

---

