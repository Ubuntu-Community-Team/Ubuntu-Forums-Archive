---
title: "Trying to install pencil, just checking if it's a system76 problem or if it's Pencil"
date: 2009-03-02
forum: System76 Support
---

### Post by NerdcoreSteve on 2009-03-02
I am trying to install a cool looking program called [Pencil]("http://www.les-stooges.org/pascal/pencil/") on my new Pangolin and want to make sure if there is something special I might need to do to make it work because I have a this cool system76 computer:P. I get an error message when I try to install pencil-0.4.3b-0ubuntu2_i386.deb using GDebi package installer. "Error: wrong architecture 'i386'". I searched for this error in the Pencil forums and didn't get a hit.

What I've tried so far:

I tried a little command line voodoo from another forum that post about the same error installing skype:

Here is the copy of a third attempt

steve@ubuntu:~/Desktop$ sudo dpkg --force-architecture -i pencil-0.4.3b-0ubuntu2_i386.deb
dpkg - warning, overriding problem because --force enabled:
package architecture (i386) does not match system (amd64)
(Reading database ... 208802 files and directories currently installed.)
Preparing to replace pencil 0.4.3b-0ubuntu2 (using pencil-0.4.3b-0ubuntu2_i386.deb) ...
Unpacking replacement pencil ...
Setting up pencil (0.4.3b-0ubuntu2) ...

it just stalls here so I type pencil to see what happens


steve@ubuntu:~/Desktop$ pencil
pencil: error while loading shared libraries: libming.so.0: cannot open shared object file: No such file or directory

This is what happens every time I type pencil in the command line now.

so I try to install libming.so.0, I already have installed libming0 from syntaptic.

I also installed: libming-dev, libming-util, libmed-dev, libmed-tools, and libmed-doc.

steve@ubuntu:~/Desktop$ sudo apt-get install libming.so.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libming.so.0


I notice that the pencil icon is in my applications menu but not thing happens when I click on it.

I've posted this problem on the Pencil forums too. Any help would be appreciated. :D

---

### Post by drewbenn on 2009-03-02
> **NerdcoreSteve said:**
> "Error: wrong architecture 'i386'"

The problem is that you have a 32-bit package, but a 64-bit operating system.  Possible solutions: get them to release a 64-bit version, get the source code and build it yourself, or install some extra packages (the most complicated; [http://whynotwiki.com/How_I_installed_N_on_64-bit_Linux](http://whynotwiki.com/How_I_installed_N_on_64-bit_Linux) for an example; I've never successfully done this).  Good luck....

---

### Post by drewbenn on 2009-03-02
Someone was trying to get it packaged for Ubuntu Studio, but looks like it never happened, [https://wiki.ubuntu.com/UbuntuStudio/IntrepidGoals](https://wiki.ubuntu.com/UbuntuStudio/IntrepidGoals).
Maybe try it in wine, per [http://www.ubuntuessentials.net/?p=580](http://www.ubuntuessentials.net/?p=580) ?
Or, perhaps, [http://www.getdeb.net/search.php?search_distro_id=10&keywords=pencil](http://www.getdeb.net/search.php?search_distro_id=10&keywords=pencil)

---

### Post by drewbenn on 2009-03-02
> **drewbenn said:**
> [http://www.getdeb.net/search.php?search_distro_id=10&keywords=pencil]("http://www.getdeb.net/search.php?search_distro_id=10&keywords=pencil")
worked for me.  That is a cool program, thanks :)

---

### Post by NerdcoreSteve on 2009-03-02
That worked for me too! Thanks a lot! Now to make some cartoons...:popcorn:

---

