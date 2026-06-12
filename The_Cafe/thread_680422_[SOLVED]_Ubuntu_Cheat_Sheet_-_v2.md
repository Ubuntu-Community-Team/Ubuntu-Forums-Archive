---
title: "[SOLVED] Ubuntu Cheat Sheet - v2"
date: 2008-01-27
forum: The Cafe
---

### Post by jpeddicord on 2008-01-27
Many of you have probably already seen this:
[http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/)

It's nice, and I don't plan on making any further modifications to it. However, looking around, there are a lot of people that want an Ubuntu-specific sheet.

Out of boredism, I drafted up a quick copy based on the Unix/Linux sheet. The final copy is planned to have at least:[LIST]
[*]Display (keyboard shortcuts, GDM, KDM, X.Org commands)
[*]APT and DPKG commands
[*]KDE/GNOME/XFCE shortcuts
[*]Magic SysRq (REISUB)
[*]Ubuntu metapackages (*-desktop, *-restricted-extras)
[*]Sudo
[*]System files (ie, /etc/init.d, /etc/sudoers)[/LIST]So that all sounds all fine and dandy. That's doesn't make many topics however. What do you think should be on the sheet? I'm a GNOME fan, but I'm unsure of all of the handy shortcuts of KDE and XFCE.

A quick note: I want to try to *not* have anything from the previous sheet (linked above) unless they can be reapplied to Ubuntu setups. I can't attribute anything on the sheet either, I imagine the space will be crammed as it is, but I'll make a note on the article itself about this.

So, again: What commands do you find useful on your system?

---

### Post by jasay on 2008-01-27
This was the cheat sheet I started with a few years ago. Print on the front and back of a page and fold in thirds. 

[http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf](http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf)

Worked pretty well for me at the time.  Has very good coverage of dpkg and apt-get.  It might give you some ideas.

---

### Post by borris.morris on 2008-01-27
ls
cd
grep
cat
rm
startx
killall
iwconfig
iwlist
ssh
ping
dhclient
dpkg
apt
aptitude

thats all i can think of right now...

---

### Post by DAE51D on 2009-02-11
> **jacobmp92 said:**
> Many of you have probably already seen this:
[URL]What commands do you find useful on your system?

dpkg -p $filename = shows info like VERSION about a package, but you don't have to know the full-on exact .deb name. "dpkg -p zip" for example.

dpkg --get-selections == shows everything installed.

apt-cache search $foo == search for a package to install.

sudo su - == switch to root account from user account.

alias ps='ps awwx'
alias killall='killall -vrI'
alias grep='grep -n -i --color=auto'

grep -R 'foo' *

alias cvsu='CURR=`pwd`;cd_pse02;cvs -q update -P -d;cd $CURR' == this one is great for developers. just be anywhere within the CVS tree and it will update your tree and not loose your directory you're in currently.

alias purge_cvs='find . -name "CVS" -type d -exec rm -rf {} \;'
will remove all the CVS directories

add these to your .bashrc

findrm() { 
	# http://wooledge.org:8000/UsingFind has some great examples
	find / -name $1 -exec rm -rf {} \; 
}

findme() { 
	find / -name $1; 
}

---

