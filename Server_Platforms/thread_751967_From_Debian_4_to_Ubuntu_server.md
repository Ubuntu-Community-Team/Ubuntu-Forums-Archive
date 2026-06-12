---
title: "From Debian 4 to Ubuntu server"
date: 2008-04-11
forum: Server Platforms
---

### Post by corrosion on 2008-04-11
Hi all,

I am using a server at home with Debian etch. I would like to try Ubuntu server and I wonder if it could be possible to update directly from etch to ubuntu server 7.10 via sources.list without having big problems with the software installed. Filesystem is working with LVM.

Thanks and regards.

---

### Post by njparton on 2008-04-11
I've never come across anyone doing this so I'd start afresh if I where you.

---

### Post by songshu on 2008-04-11
in the early days of ubuntu there were guides to do this.

basically ubuntu is still being made from debian unstable so it could work, depending on how many adjustments were made differing it from debian by the ubuntu boys and girls.

i personally would NOT do it on a production server, but if you do make a back up and let us know what happened.

just changes the sources.list
and do 
apt-get update
apt-get dist-upgrade

---

### Post by corrosion on 2008-04-11
All right, so I will wait to be in home and start a fresh install.
Thanks for your answers

---

### Post by kerry_s on 2008-04-11
why? debian is better for the server.
if you want more up to date just add lenny repo's, it will then be more up to date then ubuntu. i don't see why you would need to for a server though, you would want as stable as possible.

linux moves fast and ubuntu is a snap shot distro, things get old quick, you should stay with a rolling release like debian.

---

### Post by songshu on 2008-04-11
better is a matter of opinion offcourse.

but personally i stick with debian stable and i only upgraded to etch when it became 4.01.
and i only use backports for clamav.

after trying out the newest stuff for years i simply found that old and dusty suits me the best, but this is because i value stability above most anything else.

just asking, but what do you expect to find in Gutsy that is not in Etch?

---

### Post by corrosion on 2008-04-21
Hi all,

I just only want to try it. In my home my servers are a freebsd box and a Debian stable box. My workstation is a Gentoo and my laptop is running ubuntu 7.10@64bit.
I've been a Debian user for many years, specially as a server; and, in my opinion, it is maybe the best GNU/Linux option as a server. You can really trust Debian.
But when I use some specific OS, I like the stable version.
As I said, only just wondered how Ubuntu server is. Specially since I heard that Sun is going to support it for its servers... Maybe it is only a Debian with more updated packages, or maybe it includes some interesting things that Debian don't.

Regards.

---

### Post by songshu on 2008-04-22
> **corrosion said:**
>  or maybe it includes some interesting things that Debian don't.

Regards.

don't think so, unless there is something i don't know.
you can compare it with debian testing with some extra tasks in tasksel to set up a LAMP during install.

but offcourse curiosity can onle be tried with trying it yourself

---

### Post by netlogic on 2008-04-22
I moved to Ubuntu from Debian, because I wanted to know if I can recommend them to companies. Ubuntu has a commercial support, which is very important for many companies. 

The migration was pretty simple.
1. I backed up everything.
2. From Debian I ran dpkg --get-selections > pkg.lst to get all the package list
3. I installed Ubuntu LTS
4.  I edited apt locations to allow universal and backports
5. I used apt-cache search to see if package names from pkg.lst from Debian are similar to Ubuntu. Surprisingly, they have very similar names.
6. I manually edited few package names in pkg.lst to Ubuntu package names.
7. I imported the package names to the database 
sudo dpkg --set-selections < dpkglist.txt
sudo apt-get -y update
sudo apt-get dselect-upgrade
8. Imported the relevant configuration files to /etc
9. restored /home
10. only restored relevant files from /var/log

This method worked for me. It took me less than six hrs to migrate.

added: I am personally not in favor of having too many Linux choices. It tends to confuse many corporations who have the power and money to promote Linux. I tend to lean towards Ubuntu for the popularity now.

---

### Post by koenn on 2008-04-22
> **netlogic said:**
> I moved to Ubuntu from Debian, 
I've done similar exercises, for fun, and usually not fully installed systems but more allong the lines of installing Debian "base" (no extra tasks/packages), then change sources & do upograde; dist-upgrade

Starting from Debian 3, that usually works because all ubuntu packages will have higher version numbers. Starting from Debian 4, I had to force some packages to install without checking dependencies, to get out of a dependency loop, and I went trough a few "fix missing" and "reconfigure all" to be on the safe side.

So it depends mostly on version numbers of installed packages, plus you probably need to hand-pick a kernel image and install that separately. 

On a production server however, I'd probably prefer a reproduction-approach like the one netlogic describes.

---

