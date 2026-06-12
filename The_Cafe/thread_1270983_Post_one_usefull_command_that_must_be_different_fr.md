---
title: "Post one usefull command that must be different from other commands of other posts"
date: 2009-09-20
forum: The Cafe
---

### Post by colau on 2009-09-20
Hello,
```

sudo mkdir /media/anydrive
sudo mount /dev/sda1 /media/anydrive

```
[I][COLOR="Red"]
**Read all posts before posting.
**Command must be different.[/COLOR][/I]

---

### Post by SuperSonic4 on 2009-09-20
```
cp -Rvu /mnt/Music /media/backup
```

---

### Post by Monotoko on 2009-09-20
```
sudo su
```

---

### Post by Barrucadu on 2009-09-20
```
echo `< /dev/urandom tr -cd "[:graph:]" | head -c8`
```

Password generator.

---

### Post by sisco311 on 2009-09-20
```
notify-send -i ~/.icons/xclock.png \
"$(date +%H:%M)" \
"$(date +%d). $(date +%B) $(date +%Y), $(date +%A)"
```

---

### Post by RiceMonster on 2009-09-20
```
yes RiceMonster
```

---

### Post by colau on 2009-09-20
```

man man

```

---

### Post by sisco311 on 2009-09-20
```
sudo apt-get install funny-manpages
man rtfm
```

---

### Post by Kingsley on 2009-09-20
Change your mac address.
```

ifconfig wlan0 down && ifconfig wlan0 hw ether 00:00:00:00:00:00 && ifconfig wlan0 up

```

---

### Post by civillian on 2009-09-20
mount an ISO image:
```
mkdir -p /mnt/disk
mount -o loop disk1.iso /mnt/disk
```

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-20
uname -a 

Shows kernel version and distro

---

### Post by Keith Hedger on 2009-09-20
```
top -bn1
```

---

### Post by misfitpierce on 2009-09-20
sensors - Shows cpu temp and sometimes other various items temps

---

### Post by Bachstelze on 2009-09-20
```
echo usefull | ispell -a
```

---

### Post by MaxIBoy on 2009-09-20
> **Bachstelze said:**
> ```
echo usefull | ispell -a
```Holy crap, best answer ever!!!


```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/water/allscreens/point org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:'amplitude' double:0.3 string:'x' int32:$WAX string:'y' int32:$WAY
```Send a dbus event to Compiz, telling it to start a ripple effect at ($WAX, $WAY). I use it in a set of four scripts, which work together to make my network manager applet ripple whenever I get disconnected. Obviously you need Compiz with Dbus and Ripple enabled in order for this to work.


I was going to do this with the battery as well, but met with no success.

---

### Post by schauerlich on 2009-09-20
```
ssh <username>@<someip>
screen irssi
```

Keep a session of irssi open on another computer, which you can reattach to when needed, from anywhere. Don't annoy people with part/quit messages. :)

---

### Post by Stan_1936 on 2009-09-20
Useful? HA!

It is HIGHLY unlikely that the AVERAGE user knows what even half the commands in this thread actually do!

This thread is just about as useless as the other threads.  Sorry, but that's the way I (someone seeing this thread for the first time) see it!

---

### Post by Joeb454 on 2009-09-20
> **EDavidBurg said:**
> ```
ssh <username>@<someip>
screen irssi
```

Keep a session of irssi open on another computer, which you can reattach to when needed, from anywhere. Don't annoy people with part/quit messages. :)

Normally I have the server set up in ~/.ssh/config which means I can just do ```
ssh server
screen -Dr
```

where server has a port & user listed, key auth is set up, and the irssi session is already there :)

I guess this is just a follow on from your command...

---

### Post by kevdog on 2009-09-20
apt-cache search <package-name>

Help you look for dependencies or packages.

---

### Post by Islington on 2009-09-20
```
nohup <command here>
```
throws the command out of the terminal, so you can close it.

```
rsync
```
highly useful for making a backup copies over things that are different only.

---

### Post by MaxIBoy on 2009-09-20
> **Islington said:**
> ```
nohup <command here>
```throws the command out of the terminal, so you can close it.Isn't it safer to append &disown to the command instead?

---

### Post by earthpigg on 2009-09-20
```
df -Th -x tmpfs
```

i have it as an alias for 'dfg' in my .bashrc.

---

### Post by Islington on 2009-09-20
> **MaxIBoy said:**
> Isn't it safer to append &disown to the command instead?

possibly but nohup reports all the output in a text file.

---

### Post by MaxIBoy on 2009-09-20
As far as I know, nohup means "no hang-up," and it makes it more difficult to *cleanly* shut down the process in question, forcing you to use kill -9? I could be entirely wrong here.



```
diff file1 file2
``` Show a comparison of file1 with file2. This comes in incredibly handy-- you can even use it to create patches which will apply those differences to some entirely separate file3, assuming file3 is similar enough to file1.

```
diff -y -B --suppress-common-lines file1 file2
```This is how I usually call diff. It prints out a side-by-side comparison, ignoring blank lines and only showing lines which have changed. This way of calling it cannot be used for patches, but it is very human-readable. For example, I'm using it here to compare two versions of my kernel .config file:
[http://pastebin.com/m5d1aa5dc](http://pastebin.com/m5d1aa5dc)
You can see that my most recent changes have enabled and disabled a lot of options since I last made a backup copy, and you can see exactly which options were changed.

Yeah, I compile kernels a lot.

---

### Post by colau on 2009-09-21
To rename:
```

mv file.txt newfilename.txt

```

---

### Post by the.dark.lord on 2009-09-21
```
whatis
```

:)

```
whatis whatis
```
whatis (1)           - display manual page descriptions

---

### Post by Xbehave on 2009-09-21
```
apropos <word>
```
Gives you a list of commands to do with word.

---

### Post by Xbehave on 2009-09-21
```
touch myself
```
Check that you have permission to use a file called myself in the current directory
make me giggle

---

### Post by colau on 2009-09-21
```

sudo aptitude install htop
htop

```

---

### Post by blackmail on 2009-09-21
Ok some of these commands are quite unused, one usefull command i would want to point out, suppose you have ext3, and want to change to the ext4 filesystem, please use the following:
```
sudo gedit /etc/fstab
```
and change every thing that has ext3 to ext4, at reboot it should work properly.
ok some other command that i found usefull are:
```
sudo su
```
or
```
sudo apt-get clean
```
```
sudo apt-get autoremove package_name
``` //this removes  the package and all its dependencies
If you have an ownership problem, then please do:
```
chown -R username:username /home
```    //and now all that is in home will be owned by you and you will be able to delete it, the command may not have its parameters in order, i usually look at the man page before using a command and i am not sitting in fromt of a linux box right now.

If you would like to know more about your hdd, and you like the graohical interface type this:
```
sudo apt-get install gparted
```
and to view (well there is a place for the menu, but since it is command line)
```
sudo gparted
```

---

### Post by SomeGuyDude on 2009-09-21
Hey, I've got a wacky idea. Explain what the commands do, as well. Because some of these look useful, but I can't quite tell what they are.

---

### Post by Exodist on 2009-09-21
Extracts multiple tape archives in a single folder:

**$ find . -name "*.tar" -exec tar -xvf \{\} \;**

---

### Post by &#32 Greg on 2009-09-21
```
echo "alias rm=\'rm -i\'" >> ~/.bashrc
```

Appends an alias to the last line of your bashrc, in this case aliasing rm to rm -i

---

### Post by Xbehave on 2009-09-21
> **blackmail said:**
> 
```
sudo gedit /etc/fstab
```
```
sudo gparted
```
Do not do these, instead use
```
sudo nano /etc/fstab
sudo parted
```
or use
```
gksudo gedit /etc/fstab
gksudo gparted
```

While```
sudo su
```should be fine, but i believe that this is preferred```
sudo -i
```(something to do with environmental variables)

my new contribution is
```
pgrep <name> #lists processes named <name> (-l) for names
pkill <name> #kills processes named <name>
killall <name> #same as pkill but not for use on solaris where it will kill everything
```

---

### Post by blackmail on 2009-09-22
i have not bothered to use gksu, because it usually does not give an error, and oh well i don't like nano, so in my opinion they are better, any way for me, but nice suggestions.

---

### Post by wojox on 2009-09-22
Limit Bandwidth:

```
sudo apt-get -o Acquire::http::Dl-Limit=25 upgrade
```

---

### Post by Xbehave on 2009-09-22
> **blackmail said:**
> i have not bothered to use gksu, because it usually does not give an error, and oh well i don't like nano, so in my opinion they are better, any way for me, but nice suggestions.
I've never run into problems, but I've [read]("http://www.psychocats.net/ubuntu/graphicalsudo") that bad stuff can happen, but hey if it works it works :D. Under su systems you definitely need to use kdesu/gtksu "guicommand" instead of su -c "gui command".

anyway my command(s) of the day
```
pgrep ktorrent
ionice -c 3 -p <PID>
renice +20 <PID>
```
use pgrep to get pids of resource intensive programs and make the nice and only touch the disk in the background 
(points [unbtbu]("http://ubuntuforums.org/showpost.php?p=7989742#post7989742"), for 1 lining it)

and the reverse
```
pgrep mplayer
sudo ionice -c 1 -p <PID>
sudo renice -5 <PID>
```
(again points for [unbtbu]("http://ubuntuforums.org/showpost.php?p=7989742#post7989742"))

---

### Post by unutbu on 2009-09-22
```
PID=$(pgrep ktorrent); ionice -c 3 -p "$PID" renice +20 "$PID"
PID=$(pgrep mplayer); sudo ionice -c 1 -p "$PID"; sudo renice -5 "$PID"


```

---

### Post by kaibob on 2009-10-10
The following command takes a screenshot of the window that has the focus and saves it with a date-and-time file name. This command differs in that it does not require that the user manually select the window.

```
scrot --focus --border '%m.%d.%y at %H.%M.%S.png'
```

This only works with the version of scrot available in Karmic Koala. You can download a deb to install this version of scrot at:

[https://launchpad.net/ubuntu/+source/scrot/0.8-10/+build/1053371](https://launchpad.net/ubuntu/+source/scrot/0.8-10/+build/1053371)

I wrote a script that does the same thing with the Imagemagick import utility, but it is substantially slower.

---

### Post by KhaaL on 2009-10-10
aptitude show pkg

...i know i'm a noob :P

---

### Post by afeasfaerw23231233 on 2009-10-10
```
find /data/bittorent/ -size -500k -type f | while read FILENAME; do rm "$FILENAME"; done

```
Some good guys in this forum told me earlier this week to delete useless advertising files from torrent downloads.

---

### Post by Xbehave on 2009-10-10
> **afeasfaerw23231233 said:**
> ```
find /data/bittorent/ -size -500k -type f | while read FILENAME; do rm "$FILENAME"; done

```
Some good guys in this forum told me earlier this week to delete useless advertising files from torrent downloads.
if the torrent is still running they will be re added or if a song is ~5seconds long (depends on encoding) you will delete it.

new command:
```
dmesg | tail
```
shows you the last few system messages (useful if your laptop breaks when you move and you want to see what broke)

---

### Post by afeasfaerw23231233 on 2009-10-14
> **Xbehave said:**
> if the torrent is still running they will be re added or if a song is ~5seconds long (depends on encoding) you will delete it.


Thanks for the advice. But I only do it when the downloading has been finished.

---

