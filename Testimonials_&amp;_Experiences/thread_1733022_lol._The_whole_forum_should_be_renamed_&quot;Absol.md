---
title: "lol. The whole forum should be renamed &quot;Absolute Beginners Talk&quot;  imo."
date: 2011-04-18
forum: Testimonials &amp; Experiences
---

### Post by goscuter1 on 2011-04-18
I'm just joking. 

Kind of. 

In my experience, I should have said. Then I wouldn't be joking. If anyone cares, look at my post count, see how many questions get answered here. People are helpful and cool. I know they just don't know the answers. But that's concerning. Someone should **know **the answers. 

The problem with investigating and Googling and looking things up...is that 80% of the time, the instruction manuals are no help whatsoever. 

And therein lies the risk, a Wikipedia-like vortex trap, where each new question raises half a dozen more. 

I just Googled "kworker" as I like to know things that are unexplained and doing stuff on my system. But I discovered, 100 new questions instead, and didn't get the answer for kworker (neither did these guys yet, but hopefully they'll figure it out cause they're brighter than I am): [http://ubuntuforums.org/showpost.php?p=10692493&postcount=18](http://ubuntuforums.org/showpost.php?p=10692493&postcount=18)

Then I got around into playing with ~$ last 

Look, I've read and read, and either I'm becoming senile at a very young age, or my highly-vaunted (by my Mom) embarrassingly-high IQ is a joke. But I can't learn squat or find answers to sweet jack all. 

Maybe getting some at launchpad, but as far as experts on ubuntuforums go, I haven't had much luck so gonna hang with you fine people for awhile - if that's okay of course. 

I don't expect anyone will actually have the answers for these questions, but I'm tired of Googling the whirlpool of 'experts', so it's a freeroll from where I'm sitting...

I am currently sitting alone, on a single console, and there are no other computers in my network. And no other people on my floor of this building. No one else (physically) gets within 100 yards of my single computer (the others have died ;( - fml). Strange that they did, because the experts said nothing was wrong, whilst they were dying. Of course. 

I have no desire for Virtual consoles, so why do I have recursive X11 nonsense going on? 

[http://i.imgur.com/i95Hf.png](http://i.imgur.com/i95Hf.png)

Speaking of which, why do I have X11 at all? I'm quite fond of Gnome/Nautilus, at least when it's not crashing randomly. 

Why...oh heck this question can ask itself:

```
goscuter1@j-d:~$ last -adioxF
         (to lvl 2)   Thu Jan  1 07:00:00 1970 - Tue Apr 19 06:36:22 2011 (15082+23:36 0.0.0.0
         (to lvl 2)   Thu Jan  1 07:00:00 1970 - Thu Jan  1 07:00:00 1970  (00:00)     0.0.0.0
         system boot  Thu Jan  1 07:00:00 1970 - Tue Apr 19 06:36:22 2011 (15082+23:36 0.0.0.0

```How do I manage 26 hours in a day. On one computer. 

```
goscuter1@j-d:~$ ac -dp ; uptime
    goscuter1                            3.86
Apr 17    total        3.86
    goscuter1                           26.34
    root                                 0.36
Apr 18    total       26.70
    goscuter1                            9.01
    root                                 1.44
Today    total       10.45
 06:39:40 up 41 min,  2 users,  load average: 0.05, 0.08, 0.13

```Why is there two of me logged in right now? Why do I keep jumping around from pts to pts and tty to tty? 

```
wtmp begins Sun Apr 17 21:06:31 2011
goscuter1@j-d:~$ last -ai
goscuter pts/0        Tue Apr 19 06:00   still logged in    0.0.0.0
goscuter tty7         Tue Apr 19 05:59   still logged in    0.0.0.0
reboot   system boot  Tue Apr 19 05:58 - 06:02  (00:03)     0.0.0.0
goscuter pts/2        Tue Apr 19 03:29 - down   (02:27)     0.0.0.0
goscuter pts/1        Tue Apr 19 03:29 - 03:29  (00:00)     0.0.0.0
goscuter pts/1        Tue Apr 19 03:09 - 03:09  (00:00)     0.0.0.0
goscuter pts/0        Tue Apr 19 03:08 - 03:29  (00:21)     0.0.0.0
root     pts/1        Tue Apr 19 01:19 - 02:00  (00:40)     0.0.0.0
root     pts/0        Tue Apr 19 01:15 - 02:00  (00:45)     0.0.0.0
goscuter tty7         Tue Apr 19 01:14 - down   (04:42)     0.0.0.0
reboot   system boot  Tue Apr 19 01:14 - 05:57  (04:42)     0.0.0.0
goscuter tty2         Tue Apr 19 01:11 - 01:11  (00:00)     0.0.0.0
goscuter tty2         Tue Apr 19 01:11 - 01:11  (00:00)     0.0.0.0
goscuter tty2         Tue Apr 19 00:56 - 01:11  (00:14)     0.0.0.0
goscuter tty2         Tue Apr 19 00:56 - 00:56  (00:00)     0.0.0.0
goscuter tty2         Tue Apr 19 00:55 - 00:55  (00:00)     0.0.0.0
goscuter tty2         Tue Apr 19 00:55 - 00:55  (00:00)     0.0.0.0
goscuter pts/0        Tue Apr 19 00:28 - crash  (00:46)     0.0.0.0
goscuter pts/0        Tue Apr 19 00:16 - 00:24  (00:07)     0.0.0.0
goscuter pts/1        Mon Apr 18 20:09 - 20:09  (00:00)     0.0.0.0
goscuter pts/0        Mon Apr 18 20:08 - 23:32  (03:23)     0.0.0.0
root     pts/0        Mon Apr 18 20:08 - 20:08  (00:00)     0.0.0.0
goscuter pts/1        Mon Apr 18 12:09 - 12:20  (00:11)     0.0.0.0
root     pts/1        Mon Apr 18 12:08 - 12:09  (00:00)     0.0.0.0
goscuter pts/0        Mon Apr 18 09:31 - 10:45  (01:13)     0.0.0.0
goscuter pts/0        Mon Apr 18 08:36 - 08:50  (00:13)     0.0.0.0
root     pts/0        Mon Apr 18 07:43 - 08:03  (00:20)     0.0.0.0
goscuter pts/0        Mon Apr 18 07:02 - 07:03  (00:00)     0.0.0.0
goscuter tty7         Mon Apr 18 06:54 - crash  (18:19)     0.0.0.0
reboot   system boot  Mon Apr 18 06:54 - 05:57  (23:02)     0.0.0.0
goscuter tty7         Mon Apr 18 03:21 - crash  (03:32)     0.0.0.0
reboot   system boot  Mon Apr 18 03:21 - 05:57 (1+02:36)    0.0.0.0
goscuter pts/0        Mon Apr 18 01:13 - 02:07  (00:53)     0.0.0.0
goscuter tty7         Mon Apr 18 01:07 - 03:18  (02:11)     0.0.0.0
reboot   system boot  Mon Apr 18 01:07 - 03:18  (02:11)     0.0.0.0
goscuter pts/0        Mon Apr 18 00:54 - 00:54  (00:00)     0.0.0.0
goscuter pts/0        Mon Apr 18 00:51 - 00:52  (00:00)     0.0.0.0
goscuter pts/0        Sun Apr 17 23:30 - 23:42  (00:11)     0.0.0.0
goscuter tty7         Sun Apr 17 22:21 - down   (02:44)     0.0.0.0
reboot   system boot  Sun Apr 17 22:21 - 01:06  (02:45)     0.0.0.0
goscuter tty1         Sun Apr 17 22:20 - crash  (00:01)     0.0.0.0
goscuter tty1         Sun Apr 17 22:20 - 22:20  (00:00)     0.0.0.0
goscuter tty1         Sun Apr 17 22:18 - 22:19  (00:01)     0.0.0.0
goscuter tty1         Sun Apr 17 22:18 - 22:18  (00:00)     0.0.0.0
reboot   system boot  Sun Apr 17 22:17 - 01:06  (02:48)     0.0.0.0
reboot   system boot  Sun Apr 17 22:16 - 01:06  (02:50)     0.0.0.0
goscuter pts/1        Sun Apr 17 21:49 - 21:49  (00:00)     0.0.0.0
goscuter pts/0        Sun Apr 17 21:18 - 22:14  (00:55)     0.0.0.0
goscuter tty7         Sun Apr 17 21:17 - down   (00:57)     0.0.0.0
reboot   system boot  Sun Apr 17 21:16 - 22:14  (00:57)     0.0.0.0
goscuter tty7         Sun Apr 17 21:07 - 21:15  (00:07)     0.0.0.0
reboot   system boot  Sun Apr 17 21:06 - 21:15  (00:09)     0.0.0.0

```Here are my last 2 hours worth of commands. When I say 'my', I mean...I typed 1% of them. 

So who or what is tying the rest of them? And what is with the timing being all out of order? 

I just rebooted, like right now pretty much. My only use of the terminal after booting back in was the 5 "last" commands right there with a sudo. Who's doing these other commands? I'm sick of Googling and finding non-answers.  

WAY down the list, you'll see where I learned about ~$ sudo halt

lol. 

But my next commands after that was the bolded 6 just directly below these lines. And all those commands being entered into the terminal in the minute before I pressed "halt" - that crap is not by me. I did no such commands. This is crap, basically. 

I got like 99 problems, and ubuntu is now all of them (Windows was, before). My soon-to-be-ex-girlfriend is about to tip it to 100. I need to end this ridiculous madness. But everyone says everything is fine. No problems. No answers. 

I'm tired of asking questions. And getting no answers anyway. So I'm gonna stop. If anyone wants to look out of interest, be my guest. And I'd appreciate it, of course. 

```
cat                    goscuter __         0.00 secs Tue Apr 19 06:03
which                  goscuter __         0.00 secs Tue Apr 19 06:03
compiz            F    goscuter __         0.00 secs Tue Apr 19 06:03
[B]last                   goscuter pts/0      0.00 secs Tue Apr 19 06:02
last                   goscuter pts/0      0.00 secs Tue Apr 19 06:01
last                   goscuter pts/0      0.00 secs Tue Apr 19 06:01
sudo             S     root     pts/0      0.04 secs Tue Apr 19 06:01
last             S     root     pts/0      0.00 secs Tue Apr 19 06:01
last                   goscuter pts/0      0.00 secs Tue Apr 19 06:01[/B]
compiz            F    goscuter __         0.00 secs Tue Apr 19 06:00
desktopcouch-se   F    goscuter __         0.03 secs Tue Apr 19 05:59
tty                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
apport-checkrep        goscuter __         0.06 secs Tue Apr 19 06:00
apport-checkrep        goscuter __         0.06 secs Tue Apr 19 06:00
ps                     goscuter pts/0      0.01 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
is-cache-empty         goscuter __         0.00 secs Tue Apr 19 06:00
find                   goscuter __         0.00 secs Tue Apr 19 06:00
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 06:00
apt-check              goscuter __         0.50 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
dpkg                   goscuter __         0.00 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
dpkg                   goscuter __         0.00 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
dpkg                   goscuter __         0.00 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
dpkg                   goscuter __         0.00 secs Tue Apr 19 06:00
lsb_release            goscuter __         0.02 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
users                  goscuter pts/0      0.00 secs Tue Apr 19 06:00
whoami                 goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
ls                     goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.03 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
uname                  goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
dircolors              goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
lesspipe               goscuter pts/0      0.00 secs Tue Apr 19 06:00
lesspipe          F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
dirname                goscuter pts/0      0.00 secs Tue Apr 19 06:00
basename               goscuter pts/0      0.00 secs Tue Apr 19 06:00
compiz            F    goscuter __         0.00 secs Tue Apr 19 06:00
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 06:00
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
ubuntuone-login        goscuter __         0.29 secs Tue Apr 19 05:59
ondemand               root     __         0.00 secs Tue Apr 19 05:58
sleep                  root     __         0.00 secs Tue Apr 19 05:58
ubuntu-sso-logi        goscuter __         0.21 secs Tue Apr 19 05:59
e-addressbook-f      X goscuter __         0.01 secs Tue Apr 19 05:59
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ubuntuone-launc        goscuter __         0.35 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
couchjs           F    goscuter __         0.00 secs Tue Apr 19 05:59
sed                    goscuter __         0.00 secs Tue Apr 19 05:59
couchjs           F    goscuter __         0.00 secs Tue Apr 19 05:59
getopt                 goscuter __         0.00 secs Tue Apr 19 05:59
basename               goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
ureadahead       SF    root     __         0.21 secs Tue Apr 19 05:58
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
inet_gethost           goscuter __         0.00 secs Tue Apr 19 05:59
inet_gethost      F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
indicator-datet      X goscuter __         0.03 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sleep                  root     __         0.00 secs Tue Apr 19 05:58
python                 goscuter __         0.10 secs Tue Apr 19 05:59
lockfile-remove        root     __         0.00 secs Tue Apr 19 05:59
ubuntu-geoip-pr      X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
indicator-me-se      X goscuter __         0.01 secs Tue Apr 19 05:59
indicator-sound      X goscuter __         0.00 secs Tue Apr 19 05:59
lockfile-touch         root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d            root     __         0.00 secs Tue Apr 19 05:59
ntpdate          S     root     __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
erl               F    goscuter __         0.00 secs Tue Apr 19 05:59
sed                    goscuter __         0.00 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.04 secs Tue Apr 19 05:59
erl               F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
python                 goscuter __         0.04 secs Tue Apr 19 05:59
python                 goscuter __         0.04 secs Tue Apr 19 05:59
python                 goscuter __         0.04 secs Tue Apr 19 05:59
python                 goscuter __         0.09 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.05 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
getopt                 goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
basename               goscuter __         0.00 secs Tue Apr 19 05:59
couchdb                goscuter __         0.00 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
couchdb           F    goscuter __         0.00 secs Tue Apr 19 05:59
couchdb           F    goscuter __         0.00 secs Tue Apr 19 05:59
couchdb           F    goscuter __         0.00 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
couchdb           F    goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
getopt                 goscuter __         0.00 secs Tue Apr 19 05:59
python                 goscuter __         0.08 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
basename               goscuter __         0.00 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.02 secs Tue Apr 19 05:59
python                 goscuter __         0.02 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
net                    goscuter __         0.00 secs Tue Apr 19 05:59
gvfsd             F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
which                  goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
grep                   goscuter __         0.00 secs Tue Apr 19 05:59
lspci                  goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
grep                   goscuter __         0.00 secs Tue Apr 19 05:59
lspci                  goscuter __         0.00 secs Tue Apr 19 05:59
nm-dispatcher.a  S     root     __         0.00 secs Tue Apr 19 05:59
threaded-ml          X goscuter __         0.04 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
invoke-rc.d            root     __         0.00 secs Tue Apr 19 05:59
lockfile-create        root     __         0.00 secs Tue Apr 19 05:59
run-parts              root     __         0.00 secs Tue Apr 19 05:59
wpasupplicant          root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
wpasupplicant     F    root     __         0.00 secs Tue Apr 19 05:59
sh                     root     __         0.00 secs Tue Apr 19 05:59
sh                F    root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
status                 root     __         0.00 secs Tue Apr 19 05:59
upstart                root     __         0.00 secs Tue Apr 19 05:59
initctl                root     __         0.00 secs Tue Apr 19 05:59
openvpn                root     __         0.00 secs Tue Apr 19 05:59
ntpdate                root     __         0.00 secs Tue Apr 19 05:59
clamav-freshcla        root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch        root     __         0.00 secs Tue Apr 19 05:59
touch            S     root     __         0.00 secs Tue Apr 19 05:59
logger                 root     __         0.00 secs Tue Apr 19 05:59
killall                goscuter __         0.00 secs Tue Apr 19 05:59
invoke-rc.d            root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon           root     __         0.00 secs Tue Apr 19 05:59
stop                   root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon     SF    avahi    __         0.01 secs Tue Apr 19 05:58
avahi-daemon      F  X avahi    __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:59
status                 root     __         0.00 secs Tue Apr 19 05:59
basename               root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d       F    root     __         0.00 secs Tue Apr 19 05:59
xargs                  root     __         0.00 secs Tue Apr 19 05:59
echo                   root     __         0.00 secs Tue Apr 19 05:59
ls                     root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d       F    root     __         0.00 secs Tue Apr 19 05:59
xargs                  root     __         0.00 secs Tue Apr 19 05:59
echo                   root     __         0.00 secs Tue Apr 19 05:59
ls                     root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d       F    root     __         0.00 secs Tue Apr 19 05:59
xargs                  root     __         0.00 secs Tue Apr 19 05:59
echo                   root     __         0.00 secs Tue Apr 19 05:59
ls                     root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d       F    root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
runlevel               root     __         0.00 secs Tue Apr 19 05:59
gvfsd             F    goscuter __         0.00 secs Tue Apr 19 05:59
which                  root     __         0.00 secs Tue Apr 19 05:59
egrep                  root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
host                   root     __         0.00 secs Tue Apr 19 05:59
mv               S     root     __         0.00 secs Tue Apr 19 05:59
sort             S     root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
cat                    root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
route                  root     __         0.00 secs Tue Apr 19 05:59
zeitgeist-datah      X goscuter __         0.01 secs Tue Apr 19 05:59
which                  goscuter __         0.00 secs Tue Apr 19 05:59
start-pulseaudi        goscuter __         0.00 secs Tue Apr 19 05:59
pactl                  goscuter __         0.00 secs Tue Apr 19 05:59
pactl                  goscuter __         0.00 secs Tue Apr 19 05:59
pactl                  goscuter __         0.00 secs Tue Apr 19 05:59
pactl                  goscuter __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
egrep                  root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
ifconfig               root     __         0.00 secs Tue Apr 19 05:59
egrep                  root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
avahi-autoipd          root     __         0.00 secs Tue Apr 19 05:59
ip                     root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
ip                     root     __         0.00 secs Tue Apr 19 05:59
mv                     root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
cat                    root     __         0.00 secs Tue Apr 19 05:59
mktemp                 root     __         0.00 secs Tue Apr 19 05:59
gnome-screensav      X goscuter __         0.03 secs Tue Apr 19 05:59
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
nm-dhcp-client.        root     __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
nm-dhcp-client.        root     __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
syndaemon              goscuter __         0.00 secs Tue Apr 19 05:59
gvfsd             F    goscuter __         0.00 secs Tue Apr 19 05:59
gnome-settings-   F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
pulseaudio        F    goscuter __         0.00 secs Tue Apr 19 05:59
pulseaudio             goscuter __         0.00 secs Tue Apr 19 05:59
pulseaudio             goscuter __         0.00 secs Tue Apr 19 05:59
xdg-user-dirs-g        goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
docky             F    goscuter __         0.00 secs Tue Apr 19 05:59
dirname                goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:59
gnome-settings-        goscuter __         0.00 secs Tue Apr 19 05:59
gvfs-fuse-daemo        goscuter __         0.00 secs Tue Apr 19 05:59
fusermount       S     goscuter __         0.00 secs Tue Apr 19 05:59
mount            S     root     __         0.00 secs Tue Apr 19 05:59
gvfsd             F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
gnome-keyring-d        goscuter __         0.00 secs Tue Apr 19 05:59
gnome-keyring-d        goscuter __         0.00 secs Tue Apr 19 05:59
gnome-keyring-d        goscuter __         0.00 secs Tue Apr 19 05:59
gsettings-data-        goscuter __         0.00 secs Tue Apr 19 05:59
unity_support_t  S     goscuter __         0.11 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
gconf-sanity-ch      X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-launch       F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon            goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
readlink               goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
xdg-user-dirs-u        goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
xhost                  goscuter __         0.00 secs Tue Apr 19 05:59
id                     goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
Xsession          F    goscuter __         0.00 secs Tue Apr 19 05:59
which                  goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
uname                  goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
ls                     goscuter __         0.00 secs Tue Apr 19 05:59
Xsession          F    goscuter __         0.00 secs Tue Apr 19 05:59
Xsession          F    goscuter __         0.00 secs Tue Apr 19 05:59
id                     goscuter __         0.00 secs Tue Apr 19 05:59
Default                root     __         0.00 secs Tue Apr 19 05:59
initctl                root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_probe   F    root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_test    F    root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
udev-acl.ck            root     __         0.00 secs Tue Apr 19 05:59
pam-foreground-        root     __         0.00 secs Tue Apr 19 05:59
mkdir                  root     __         0.00 secs Tue Apr 19 05:59
pam-foreground-   F    root     __         0.00 secs Tue Apr 19 05:59
cut                    root     __         0.00 secs Tue Apr 19 05:59
getent                 root     __         0.00 secs Tue Apr 19 05:59
ck-collect-sess  S     root     __         0.00 secs Tue Apr 19 05:59
ck-get-x11-serv  S     root     __         0.00 secs Tue Apr 19 05:59
gnome-settings-   F  X gdm      __         0.21 secs Tue Apr 19 05:58
gconfd-2               gdm      __         0.08 secs Tue Apr 19 05:58
dbus-daemon       F  X gdm      __         0.00 secs Tue Apr 19 05:58
gvfsd                X gdm      __         0.00 secs Tue Apr 19 05:58
udev-acl.ck            root     __         0.00 secs Tue Apr 19 05:59
pam-foreground-        root     __         0.00 secs Tue Apr 19 05:59
rm                     root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
pam-foreground-   F    root     __         0.00 secs Tue Apr 19 05:59
cut                    root     __         0.00 secs Tue Apr 19 05:59
getent                 root     __         0.00 secs Tue Apr 19 05:59
gnome-session    S   X gdm      __         0.03 secs Tue Apr 19 05:58
gconftool-2          X gdm      __         0.00 secs Tue Apr 19 05:59
metacity             X gdm      __         0.06 secs Tue Apr 19 05:58
gnome-power-man      X gdm      __         0.03 secs Tue Apr 19 05:58
gdm-simple-gree      X gdm      __         0.15 secs Tue Apr 19 05:58
gnome-keyring-d  S     goscuter __         0.00 secs Tue Apr 19 05:59
gnome-keyring-d   F    goscuter __         0.00 secs Tue Apr 19 05:59
mount.ecryptfs_  S     goscuter __         0.00 secs Tue Apr 19 05:59
cryptomgr_probe   F    root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_test    F    root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe         S     root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_test    F    root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_test    F    root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
gdm-session-wor  SF    goscuter __         1.18 secs Tue Apr 19 05:59
xkbcomp                gdm      __         0.01 secs Tue Apr 19 05:59
pm-powersave           root     __         0.00 secs Tue Apr 19 05:58
rm                     root     __         0.00 secs Tue Apr 19 05:59
xfs_buffer             root     __         0.00 secs Tue Apr 19 05:59
wireless               root     __         0.00 secs Tue Apr 19 05:59
which                  root     __         0.00 secs Tue Apr 19 05:59
which                  root     __         0.00 secs Tue Apr 19 05:59
sched-powersave        root     __         0.00 secs Tue Apr 19 05:59
sata_alpm              root     __         0.00 secs Tue Apr 19 05:59
uname                  root     __         0.00 secs Tue Apr 19 05:59
readahead              root     __         0.00 secs Tue Apr 19 05:59
blockdev         S     root     __         0.00 secs Tue Apr 19 05:59
awk                    root     __         0.00 secs Tue Apr 19 05:59
pcie_aspm              root     __         0.00 secs Tue Apr 19 05:59
laptop-mode            root     __         0.00 secs Tue Apr 19 05:59
journal-commit         root     __         0.00 secs Tue Apr 19 05:59
mount            S     root     __         0.00 secs Tue Apr 19 05:59
xkbcomp                gdm      __         0.01 secs Tue Apr 19 05:59
xkbcomp                gdm      __         0.01 secs Tue Apr 19 05:59
dbus-send              gdm      __         0.00 secs Tue Apr 19 05:59
gdm-simple-gree   F    gdm      __         0.00 secs Tue Apr 19 05:59
lsb_release            gdm      __         0.02 secs Tue Apr 19 05:59
intel-audio-pow        root     __         0.00 secs Tue Apr 19 05:59
hal-cd-polling         root     __         0.00 secs Tue Apr 19 05:59
disable_wol            root     __         0.00 secs Tue Apr 19 05:59
anacron           F    root     __         0.00 secs Tue Apr 19 05:59
anacron                root     __         0.00 secs Tue Apr 19 05:59
start                  root     __         0.00 secs Tue Apr 19 05:59
anacron                root     __         0.00 secs Tue Apr 19 05:59
xkbcomp                gdm      __         0.00 secs Tue Apr 19 05:59
95hdparm-apm           root     __         0.00 secs Tue Apr 19 05:59
95hdparm-apm      F    root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
udevadm                root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
hdparm           S     root     __         0.00 secs Tue Apr 19 05:59
95hdparm-apm      F    root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
udevadm                root     __         0.00 secs Tue Apr 19 05:59
95hdparm-apm      F    root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
gnome-power-bac        gdm      __         0.00 secs Tue Apr 19 05:59
pm-powersave      F    root     __         0.00 secs Tue Apr 19 05:59
uniq                   root     __         0.00 secs Tue Apr 19 05:59
sort                   root     __         0.00 secs Tue Apr 19 05:59
pm-powersave      F    root     __         0.00 secs Tue Apr 19 05:58
rm                     root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
flock                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
upowerd           F    root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported        root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported   F    root     __         0.00 secs Tue Apr 19 05:58
tr                     root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported   F    root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported        root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported   F    root     __         0.00 secs Tue Apr 19 05:58
tr                     root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported   F    root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:58
gnome-settings-        gdm      __         0.00 secs Tue Apr 19 05:58
dbus-daemon       F  X gdm      __         0.00 secs Tue Apr 19 05:58
dbus-daemon       F  X gdm      __         0.00 secs Tue Apr 19 05:58
gconf-sanity-ch      X gdm      __         0.01 secs Tue Apr 19 05:58
dbus-launch       F    gdm      __         0.00 secs Tue Apr 19 05:58
dbus-launch      S     gdm      __         0.00 secs Tue Apr 19 05:58
dbus-launch       F    gdm      __         0.00 secs Tue Apr 19 05:58
dbus-daemon            gdm      __         0.02 secs Tue Apr 19 05:58
udev-acl.ck            root     __         0.00 secs Tue Apr 19 05:58
pam-foreground-        root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
pam-foreground-   F    root     __         0.00 secs Tue Apr 19 05:58
cut                    root     __         0.00 secs Tue Apr 19 05:58
getent                 root     __         0.00 secs Tue Apr 19 05:58
ck-collect-sess        root     __         0.00 secs Tue Apr 19 05:58
Default                root     __         0.00 secs Tue Apr 19 05:58
Default           F    root     __         0.00 secs Tue Apr 19 05:58
uname                  root     __         0.00 secs Tue Apr 19 05:58
Default           F    root     __         0.00 secs Tue Apr 19 05:58
Default           F    root     __         0.00 secs Tue Apr 19 05:58
initctl                root     __         0.00 secs Tue Apr 19 05:58
setvtrgb         S     root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
ck-get-x11-disp  S     root     __         0.00 secs Tue Apr 19 05:58
rc                     root     __         0.00 secs Tue Apr 19 05:58
S99rc.local            root     __         0.00 secs Tue Apr 19 05:58
rc.local               root     __         0.00 secs Tue Apr 19 05:58
plymouthd        SF    root     __         0.36 secs Tue Apr 19 05:58
plymouth-upstar  S     root     __         0.30 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
egrep            S     root     __         0.00 secs Tue Apr 19 05:58
egrep                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
start-stop-daem   F    root     __         0.00 secs Tue Apr 19 05:58
S99ondemand            root     __         0.00 secs Tue Apr 19 05:58
start-stop-daem  S     root     __         0.00 secs Tue Apr 19 05:58
egrep            S     root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
S99grub-common         root     __         0.00 secs Tue Apr 19 05:58
grub-editenv           root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
egrep            S     root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
which                  root     __         0.00 secs Tue Apr 19 05:58
S90binfmt-suppo  S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
update-binfmts         root     __         0.00 secs Tue Apr 19 05:58
mount            S     root     __         0.00 secs Tue Apr 19 05:58
modprobe         S     root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
which                  root     __         0.00 secs Tue Apr 19 05:58
uname                  root     __         0.00 secs Tue Apr 19 05:58
S75sudo                root     __         0.00 secs Tue Apr 19 05:58
find             S     root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
0000usepeerdns         root     __         0.00 secs Tue Apr 19 05:58
readlink               root     __         0.00 secs Tue Apr 19 05:58
S70dns-clean           root     __         0.00 secs Tue Apr 19 05:58
0dns-down              root     __         0.00 secs Tue Apr 19 05:58
0dns-down         F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
ls                     root     __         0.00 secs Tue Apr 19 05:58
0dns-down         F    root     __         0.00 secs Tue Apr 19 05:58
cut                    root     __         0.00 secs Tue Apr 19 05:58
0dns-down         F    root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
S50saned               root     __         0.00 secs Tue Apr 19 05:58
S50rsync               root     __         0.00 secs Tue Apr 19 05:58
S50pulseaudio    S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
S31atieventsd          root     __         0.00 secs Tue Apr 19 05:58
S25openafs-clie        root     __         0.00 secs Tue Apr 19 05:58
fs               S     root     __         0.00 secs Tue Apr 19 05:58
afsd             S     root     __         0.04 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd              F    root     __         0.00 secs Tue Apr 19 05:58
pidof            S     root     __         0.00 secs Tue Apr 19 05:58
pidof            S     root     __         0.00 secs Tue Apr 19 05:58
modprobe         S     root     __         0.00 secs Tue Apr 19 05:58
S25openafs-clie   F    root     __         0.00 secs Tue Apr 19 05:58
fgrep                  root     __         0.00 secs Tue Apr 19 05:58
lsmod                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
uname                  root     __         0.00 secs Tue Apr 19 05:58
uname                  root     __         0.00 secs Tue Apr 19 05:58
S20speech-dispa        root     __         0.00 secs Tue Apr 19 05:58
S20plymouth-ups        root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20plymouth            root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20network-mana        root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20kerneloops    S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
pidof            S     root     __         0.00 secs Tue Apr 19 05:58
kerneloops       S     kernoops __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
udev-configure-   F    root     __         0.00 secs Tue Apr 19 05:58
python           S   X lp       __         0.20 secs Tue Apr 19 05:58
cups-deviced     S     root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20isc-dhcp-ser  S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
sleep                  root     __         0.00 secs Tue Apr 19 05:58
modprobe               root     tty7       0.00 secs Tue Apr 19 05:58
hp               S     lp       __         0.00 secs Tue Apr 19 05:58
usb                    root     __         0.00 secs Tue Apr 19 05:58
serial                 root     __         0.00 secs Tue Apr 19 05:58
dhcpd            S     dhcpd    __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
dhcpd            S     dhcpd    __         0.00 secs Tue Apr 19 05:58
S20hostname            root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20gdm                 root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20cron                root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh  S     root     __         0.01 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
freshclam        S     clamav   __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.01 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.01 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udev-configure-   F    root     __         0.00 secs Tue Apr 19 05:58
sh                     root     __         0.00 secs Tue Apr 19 05:58
udev-configure-        root     __         0.00 secs Tue Apr 19 05:58
udev-configure-        root     __         0.00 secs Tue Apr 19 05:58
sh                F    root     __         0.00 secs Tue Apr 19 05:58
udevadm                root     __         0.00 secs Tue Apr 19 05:58
udevadm                root     __         0.00 secs Tue Apr 19 05:58
sleep                  root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
pidof            S     root     __         0.00 secs Tue Apr 19 05:58
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
dirname                root     __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
sh                     root     __         0.00 secs Tue Apr 19 05:58
chgrp                  root     __         0.00 secs Tue Apr 19 05:58
dmesg                  root     __         0.00 secs Tue Apr 19 05:58
sleep                  root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
egrep                  root     __         0.00 secs Tue Apr 19 05:58
savelog                root     __         0.00 secs Tue Apr 19 05:58
mv                     root     __         0.00 secs Tue Apr 19 05:58
ln                     root     __         0.00 secs Tue Apr 19 05:58
S20bootlogd            root     __         0.00 secs Tue Apr 19 05:58
egrep            S     root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
S20avahi-daemon        root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20anacron             root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
chmod            S     root     __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
S20acct                root     __         0.00 secs Tue Apr 19 05:58
accton           S     root     __         0.00 secs Tue Apr 19 05:58
plymouthd              root     __         0.00 secs Tue Apr 19 05:57
gdm-binary       S   X root     __         0.02 secs Tue Apr 19 01:14
gdm-simple-slav  S   X root     __         0.01 secs Tue Apr 19 01:14
Xorg             S     root     tty7     664.72 secs Tue Apr 19 01:14
S20sendsigs       F    root     __         0.00 secs Tue Apr 19 05:57
sed                    root     __         0.00 secs Tue Apr 19 05:57
initctl                root     __         0.00 secs Tue Apr 19 05:57
S10unattended-u        root     __         0.00 secs Tue Apr 19 05:57
python           S     root     __         0.02 secs Tue Apr 19 05:57
firegl            F    root     __         0.00 secs Tue Apr 19 01:14
firegl            F    root     __         0.00 secs Tue Apr 19 01:14
firegl            F    root     __         0.00 secs Tue Apr 19 01:14
K80openvpn       S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
ls                     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
K31atieventsd          root     __         0.00 secs Tue Apr 19 05:57
K20speech-dispa        root     __         0.00 secs Tue Apr 19 05:57
K20plymouth-ups        root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20plymouth            root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20openafs-clie        root     __         0.00 secs Tue Apr 19 05:57
K20openafs-clie   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
lsmod                  root     __         0.00 secs Tue Apr 19 05:57
start-stop-daem  S     root     __         0.00 secs Tue Apr 19 05:57
pidof            S     root     __         0.00 secs Tue Apr 19 05:57
pidof            S     root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
uname                  root     __         0.00 secs Tue Apr 19 05:57
K20network-mana        root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20isc-dhcp-ser  S     root     __         0.00 secs Tue Apr 19 05:57
rm               S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
start-stop-daem        root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
K20hostname            root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20gdm                 root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20cron                root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh  S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
sleep                  root     __         0.00 secs Tue Apr 19 05:57
compiz           S   X goscuter __       226.35 secs Tue Apr 19 01:14
desktopcouch-se   F    goscuter __         8.23 secs Tue Apr 19 01:15
kerneloops        F    kernoops __         0.33 secs Tue Apr 19 01:14
dbus-daemon      SF  X root     __         0.00 secs Tue Apr 19 01:15
sh                     goscuter __         0.00 secs Tue Apr 19 01:15
unity-window-de      X goscuter __        12.59 secs Tue Apr 19 01:15
gdu-notificatio        goscuter __         0.02 secs Tue Apr 19 01:15
bash                   goscuter pts/2      0.22 secs Tue Apr 19 03:29
gnome-pty-helpe        goscuter __         0.00 secs Tue Apr 19 03:08
shutter              X goscuter __         3.90 secs Tue Apr 19 01:14
docky                X goscuter __        72.17 secs Tue Apr 19 01:14
gnome-screensav   F    goscuter __         0.03 secs Tue Apr 19 01:15
notify-osd           X goscuter __         4.46 secs Tue Apr 19 01:14
ssh-agent         F    goscuter __         0.00 secs Tue Apr 19 01:14
gvfs-fuse-daemo   F    goscuter __         0.01 secs Tue Apr 19 01:14
fusermount       S     goscuter __         0.00 secs Tue Apr 19 05:57
umount           S     root     __         0.00 secs Tue Apr 19 05:57
soffice.bin          X goscuter __        34.07 secs Tue Apr 19 04:36
nm-applet            X goscuter __         0.73 secs Tue Apr 19 01:14
gconfd-2               goscuter __         2.48 secs Tue Apr 19 01:14
modem-manager    S     root     __         0.01 secs Tue Apr 19 01:14
polkitd          S   X root     __         1.20 secs Tue Apr 19 01:14
console-kit-dae  S   X root     __         0.23 secs Tue Apr 19 01:14
udisks-daemon    S   X root     __         0.29 secs Tue Apr 19 01:14
system-service-  S   X root     __         0.07 secs Tue Apr 19 01:16
dbus-daemon      SF  X messageb __         1.04 secs Tue Apr 19 01:14
wpa_supplicant   S     root     __         0.00 secs Tue Apr 19 01:14
upowerd          S   X root     __         0.03 secs Tue Apr 19 01:14
udisks-daemon     F  X root     __         1.00 secs Tue Apr 19 01:14
rtkit-daemon     S   X rtkit    __         0.04 secs Tue Apr 19 01:14
hwclock          S     root     __         0.26 secs Tue Apr 19 05:57
flush-0:21        F    root     __         0.00 secs Tue Apr 19 05:57
firefox-bin          X goscuter __       1537.68 secs Tue Apr 19 01:18
plugin-containe      X goscuter __       162.63 secs Tue Apr 19 01:19
unity-panel-ser      X goscuter __       119.13 secs Tue Apr 19 01:15
gedit                X goscuter __        27.97 secs Tue Apr 19 03:47
indicator-appli      X goscuter __         0.42 secs Tue Apr 19 01:15
geoclue-master       X goscuter __         0.03 secs Tue Apr 19 01:15
unity-files-dae      X goscuter __         0.74 secs Tue Apr 19 01:15
indicator-sessi      X goscuter __         0.03 secs Tue Apr 19 01:15
indicator-datet      X goscuter __         0.03 secs Tue Apr 19 01:15
indicator-messa      X goscuter __         0.03 secs Tue Apr 19 01:15
indicator-me-se      X goscuter __         0.04 secs Tue Apr 19 01:15
nautilus             X goscuter __       269.51 secs Tue Apr 19 01:14
gvfsd-metadata         goscuter __         0.02 secs Tue Apr 19 01:15
dconf-service        X goscuter __         0.07 secs Tue Apr 19 01:15
vino-server          X goscuter __         1.48 secs Tue Apr 19 01:14
update-notifier      X goscuter __         0.31 secs Tue Apr 19 01:15
indicator-sound      X goscuter __         0.13 secs Tue Apr 19 01:15
ubuntuone-syncd      X goscuter __        13.70 secs Tue Apr 19 01:15
unity-applicati      X goscuter __         0.50 secs Tue Apr 19 01:15
gnome-terminal       X goscuter __        21.71 secs Tue Apr 19 03:08
desktopcouch-se        goscuter __         8.94 secs Tue Apr 19 01:15
gvfsd-computer         goscuter __         0.01 secs Tue Apr 19 01:15
indicator-weath      X goscuter __         1.80 secs Tue Apr 19 01:14
mission-control        goscuter __         0.03 secs Tue Apr 19 01:15
gvfs-afc-volume      X goscuter __         0.00 secs Tue Apr 19 01:14
polkit-gnome-au      X goscuter __         0.20 secs Tue Apr 19 01:14
cat                    goscuter __         0.00 secs Tue Apr 19 01:15
applet.py              goscuter __         4.01 secs Tue Apr 19 01:15
zeitgeist-daemo      X goscuter __         6.06 secs Tue Apr 19 01:14
zeitgeist-datah      X goscuter __         0.12 secs Tue Apr 19 01:14
gvfsd-burn             goscuter __         0.00 secs Tue Apr 19 01:15
gvfs-gphoto2-vo        goscuter __         0.00 secs Tue Apr 19 01:15
gvfsd-trash            goscuter __         0.03 secs Tue Apr 19 01:15
gvfs-gdu-volume        goscuter __         0.04 secs Tue Apr 19 01:14
gvfsd                  goscuter __         0.92 secs Tue Apr 19 01:14
freshclam         F    clamav   __         6.34 secs Tue Apr 19 01:14
tput             S     root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh  SF    root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh  SF    root     __         0.00 secs Tue Apr 19 05:57
dirname                root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
alsa-source       F  X goscuter __         0.11 secs Tue Apr 19 01:14
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
egrep                  root     __         0.00 secs Tue Apr 19 05:57
gconf-helper         X goscuter __         0.00 secs Tue Apr 19 01:14
gnome-settings-   F  X goscuter __         6.28 secs Tue Apr 19 01:14
gnome-session    S   X goscuter __         0.11 secs Tue Apr 19 01:14
dbus-daemon       F  X goscuter __        14.62 secs Tue Apr 19 01:14
bamfdaemon             goscuter __         2.45 secs Tue Apr 19 01:15
K20bootlogd            root     __         0.00 secs Tue Apr 19 05:57
egrep            S     root     __         0.00 secs Tue Apr 19 05:57
Default                root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
K20avahi-daemon        root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20anacron             root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
upstart-udev-br   F    root     __         0.07 secs Tue Apr 19 01:14
alsactl          S     root     __         0.01 secs Tue Apr 19 05:57
udev-acl.ck            root     __         0.00 secs Tue Apr 19 05:57
sh                     root     __         0.00 secs Tue Apr 19 05:57
sh                     root     __         0.00 secs Tue Apr 19 05:57
dd                     root     __         0.00 secs Tue Apr 19 05:57
stat                   root     __         0.00 secs Tue Apr 19 05:57
sh                F    root     __         0.00 secs Tue Apr 19 05:57
sed                    root     __         0.00 secs Tue Apr 19 05:57
pam-foreground-        root     __         0.00 secs Tue Apr 19 05:57
rm                     root     __         0.00 secs Tue Apr 19 05:57
sh                F    root     __         0.00 secs Tue Apr 19 05:57
sed                    root     __         0.00 secs Tue Apr 19 05:57
NetworkManager   SF  X root     __         0.34 secs Tue Apr 19 01:14
pam-foreground-   F    root     __         0.00 secs Tue Apr 19 05:57
cut                    root     __         0.00 secs Tue Apr 19 05:57
getent                 root     __         0.00 secs Tue Apr 19 05:57
getty                X root     tty6       0.00 secs Tue Apr 19 01:14
plymouth-upstar  S     root     __         0.00 secs Tue Apr 19 05:57
getty                X root     tty1       0.00 secs Tue Apr 19 01:14
gnome-keyring-d   F  X goscuter __         0.10 secs Tue Apr 19 01:14
getty                X root     tty3       0.00 secs Tue Apr 19 01:14
getty                X root     tty2       0.00 secs Tue Apr 19 01:14
cupsd            S     root     __         0.03 secs Tue Apr 19 01:14
upstart-socket-   F    root     __         0.02 secs Tue Apr 19 01:14
gdm-session-wor  S   X root     __         0.06 secs Tue Apr 19 01:14
acpid            SF    root     __         0.00 secs Tue Apr 19 01:14
cron              F  X root     __         0.01 secs Tue Apr 19 01:14
basename               root     __         0.00 secs Tue Apr 19 05:57
atd               F    root     __         0.00 secs Tue Apr 19 01:14
getty                X root     tty5       0.00 secs Tue Apr 19 01:14
irqbalance       SF  X root     __         6.78 secs Tue Apr 19 01:14
stty             S     root     __         0.00 secs Tue Apr 19 05:57
rsyslogd         SF    syslog   __         0.06 secs Tue Apr 19 01:14
udevd            SF    root     __         0.00 secs Tue Apr 19 01:14
udevd            SF    root     __         0.05 secs Tue Apr 19 01:14
udevd            SF    root     __         0.00 secs Tue Apr 19 01:14
getty                X root     tty4       0.00 secs Tue Apr 19 01:14
shutdown         SF    root     pts/2      0.00 secs Tue Apr 19 05:57
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:57
shutdown         S     root     pts/2      0.00 secs Tue Apr 19 05:57
[COLOR=Black]**halt                   goscuter pts/2      0.00 secs Tue Apr 19 05:57**[/COLOR]
[B][COLOR=Red]info                 X goscuter pts/2      0.00 secs Tue Apr 19 05:56
man                    goscuter pts/2      0.01 secs Tue Apr 19 05:56
pager                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
col                    goscuter pts/2      0.00 secs Tue Apr 19 05:56
nroff                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
groff                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
grotty                 goscuter pts/2      0.01 secs Tue Apr 19 05:56
troff                  goscuter pts/2      0.02 secs Tue Apr 19 05:56
tbl                    goscuter pts/2      0.00 secs Tue Apr 19 05:56
preconv                goscuter pts/2      0.00 secs Tue Apr 19 05:56
locale                 goscuter pts/2      0.00 secs Tue Apr 19 05:56[/COLOR][/B]
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
kworker/2:3       F    root     __         0.00 secs Tue Apr 19 05:51
kworker/2:2       F    root     __         0.00 secs Tue Apr 19 05:51
kworker/6:0       F    root     __         0.00 secs Tue Apr 19 04:09
whoami                 goscuter pts/2      0.00 secs Tue Apr 19 05:55
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:55
users            S     root     pts/2      0.00 secs Tue Apr 19 05:55
users                  goscuter pts/2      0.00 secs Tue Apr 19 05:55
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:45
ls                     goscuter pts/2      0.00 secs Tue Apr 19 05:55
ls                     goscuter pts/2      0.00 secs Tue Apr 19 05:55
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 05:55
python                 goscuter pts/2      0.13 secs Tue Apr 19 05:55
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 05:55
python                 goscuter pts/2      0.14 secs Tue Apr 19 05:55
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:55
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:54
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:54
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:54
kworker/1:3       F    root     __         0.00 secs Tue Apr 19 05:46
kworker/5:3       F    root     __         0.00 secs Tue Apr 19 05:48
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:53
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:53
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:53
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:53
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:53
kworker/0:0       F    root     __         0.01 secs Tue Apr 19 05:43
kworker/5:2       F    root     __         0.00 secs Tue Apr 19 05:22
kworker/1:0       F    root     __         0.00 secs Tue Apr 19 05:46
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:50
last             S     root     pts/2      0.00 secs Tue Apr 19 05:50
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:50
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 05:40
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:50
lastb                  goscuter pts/2      0.00 secs Tue Apr 19 05:48
kworker/0:2       F    root     __         0.00 secs Tue Apr 19 05:38
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:47
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:47
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:34
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:45
last             S     root     pts/2      0.00 secs Tue Apr 19 05:45
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:43
last             S     root     pts/2      0.00 secs Tue Apr 19 05:43
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:43
last             S     root     pts/2      0.00 secs Tue Apr 19 05:43
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 05:33
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:43
last             S     root     pts/2      0.01 secs Tue Apr 19 05:43
sudo             S     root     pts/2      0.04 secs Tue Apr 19 05:42
last             S     root     pts/2      0.00 secs Tue Apr 19 05:42
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:41
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:17
powertop         S     root     pts/2      1.48 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
sh                     root     pts/2      0.00 secs Tue Apr 19 05:41
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
sh                     root     pts/2      0.00 secs Tue Apr 19 05:40
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
sh                     root     pts/2      0.00 secs Tue Apr 19 05:40
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
sh                     root     pts/2      0.00 secs Tue Apr 19 05:40
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
sh                     root     pts/2      0.00 secs Tue Apr 19 05:40
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
sh                     root     pts/2      0.00 secs Tue Apr 19 05:39
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
sh                     root     pts/2      0.00 secs Tue Apr 19 05:39
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
sh                     root     pts/2      0.00 secs Tue Apr 19 05:39
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
sh                     root     pts/2      0.00 secs Tue Apr 19 05:38
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
sh                     root     pts/2      0.00 secs Tue Apr 19 05:38
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
sh                     root     pts/2      0.00 secs Tue Apr 19 05:38
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
sh                     root     pts/2      0.00 secs Tue Apr 19 05:38
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/0:2       F    root     __         0.01 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
sh                     root     pts/2      0.00 secs Tue Apr 19 05:36
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
sh                     root     pts/2      0.00 secs Tue Apr 19 05:36
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
sh                     root     pts/2      0.00 secs Tue Apr 19 05:36
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
sh                     root     pts/2      0.00 secs Tue Apr 19 05:35
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
sh                     root     pts/2      0.00 secs Tue Apr 19 05:35
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
sh                     root     pts/2      0.00 secs Tue Apr 19 05:35
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
sh                     root     pts/2      0.00 secs Tue Apr 19 05:35
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
sh                     root     pts/2      0.00 secs Tue Apr 19 05:34
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
sh                     root     pts/2      0.00 secs Tue Apr 19 05:34
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
sh                     root     pts/2      0.00 secs Tue Apr 19 05:34
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
sh                     root     pts/2      0.00 secs Tue Apr 19 05:34
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
sh                     root     pts/2      0.00 secs Tue Apr 19 05:33
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
sh                     root     pts/2      0.00 secs Tue Apr 19 05:33
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
sh                     root     pts/2      0.00 secs Tue Apr 19 05:33
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
sh                     root     pts/2      0.00 secs Tue Apr 19 05:32
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
sh                     root     pts/2      0.00 secs Tue Apr 19 05:32
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
sh                     root     pts/2      0.00 secs Tue Apr 19 05:32
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
sh                     root     pts/2      0.00 secs Tue Apr 19 05:32
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
sh                     root     pts/2      0.00 secs Tue Apr 19 05:31
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
sh                     root     pts/2      0.00 secs Tue Apr 19 05:31
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
sh                     root     pts/2      0.00 secs Tue Apr 19 05:31
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
sh                     root     pts/2      0.00 secs Tue Apr 19 05:30
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
sh                     root     pts/2      0.00 secs Tue Apr 19 05:30
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
sh                     root     pts/2      0.00 secs Tue Apr 19 05:30
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
sh                     root     pts/2      0.00 secs Tue Apr 19 05:29
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
sh                     root     pts/2      0.00 secs Tue Apr 19 05:29
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
sh                     root     pts/2      0.00 secs Tue Apr 19 05:29
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
sh                     root     pts/2      0.00 secs Tue Apr 19 05:29
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
sh                     root     pts/2      0.00 secs Tue Apr 19 05:28
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
sh                     root     pts/2      0.00 secs Tue Apr 19 05:28
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
sh                     root     pts/2      0.00 secs Tue Apr 19 05:28
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/0:2       F    root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
sh                     root     pts/2      0.00 secs Tue Apr 19 05:27
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/1:3       F    root     __         0.00 secs Tue Apr 19 05:22
kworker/1:0       F    root     __         0.00 secs Tue Apr 19 05:22
kworker/5:0       F    root     __         0.00 secs Tue Apr 19 02:06
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
sh                     root     pts/2      0.00 secs Tue Apr 19 05:27
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
sh                     root     pts/2      0.00 secs Tue Apr 19 05:27
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
sh                     root     pts/2      0.00 secs Tue Apr 19 05:26
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
sh                     root     pts/2      0.00 secs Tue Apr 19 05:26
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
sh                     root     pts/2      0.00 secs Tue Apr 19 05:26
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
sh                     root     pts/2      0.00 secs Tue Apr 19 05:25
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
sh                     root     pts/2      0.00 secs Tue Apr 19 05:25
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
sh                     root     pts/2      0.00 secs Tue Apr 19 05:25
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
sh                     root     pts/2      0.00 secs Tue Apr 19 05:25
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
sh                     root     pts/2      0.00 secs Tue Apr 19 05:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
sh                     root     pts/2      0.00 secs Tue Apr 19 05:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
sh                     root     pts/2      0.00 secs Tue Apr 19 05:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:13
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
sh                     root     pts/2      0.00 secs Tue Apr 19 05:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
sh                     root     pts/2      0.00 secs Tue Apr 19 05:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
sh                     root     pts/2      0.00 secs Tue Apr 19 05:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
sh                     root     pts/2      0.00 secs Tue Apr 19 05:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/0:0       F    root     __         0.01 secs Tue Apr 19 05:12
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
sh                     root     pts/2      0.00 secs Tue Apr 19 05:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
sh                     root     pts/2      0.00 secs Tue Apr 19 05:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
sh                     root     pts/2      0.00 secs Tue Apr 19 05:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
sh                     root     pts/2      0.00 secs Tue Apr 19 05:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
sh                     root     pts/2      0.00 secs Tue Apr 19 05:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
sh                     root     pts/2      0.00 secs Tue Apr 19 05:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
sh                     root     pts/2      0.00 secs Tue Apr 19 05:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
sh                     root     pts/2      0.00 secs Tue Apr 19 05:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
sh                     root     pts/2      0.00 secs Tue Apr 19 05:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
sh                     root     pts/2      0.00 secs Tue Apr 19 05:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
sh                     root     pts/2      0.00 secs Tue Apr 19 05:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
sh                     root     pts/2      0.00 secs Tue Apr 19 05:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
sh                     root     pts/2      0.00 secs Tue Apr 19 05:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
sh                     root     pts/2      0.00 secs Tue Apr 19 05:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 05:08
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
sh                     root     pts/2      0.00 secs Tue Apr 19 05:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
sh                     root     pts/2      0.00 secs Tue Apr 19 05:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
sh                     root     pts/2      0.00 secs Tue Apr 19 05:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
sh                     root     pts/2      0.00 secs Tue Apr 19 05:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/0:2       F    root     __         0.01 secs Tue Apr 19 05:07
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
xrandr           S     root     pts/2      0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
iwpriv                 root     pts/2      0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.06 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.05 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.03 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.06 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
modprobe               root     pts/2      0.00 secs Tue Apr 19 05:17
cron             SF    root     __         0.00 secs Tue Apr 19 05:17
sh               S     root     __         0.00 secs Tue Apr 19 05:17
run-parts              root     __         0.00 secs Tue Apr 19 05:17
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 05:14
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:03
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 05:02
grep                   goscuter pts/2      0.00 secs Tue Apr 19 05:12
grep                   goscuter pts/2      0.00 secs Tue Apr 19 05:11
uname                  goscuter pts/2      0.00 secs Tue Apr 19 05:11
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:57
grep                   goscuter pts/2      0.00 secs Tue Apr 19 05:08
ps                     goscuter pts/2      0.00 secs Tue Apr 19 05:08
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:07
grep             S   X root     pts/2      0.01 secs Tue Apr 19 05:07
kworker/0:2       F    root     __         0.00 secs Tue Apr 19 04:57
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:04
lastcomm         S     root     pts/2      0.00 secs Tue Apr 19 05:04
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:52
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:52
sudo             S     root     pts/2      0.10 secs Tue Apr 19 05:01
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:01
iwpriv                 goscuter pts/2      0.00 secs Tue Apr 19 05:00
domainname             goscuter __         0.00 secs Tue Apr 19 04:59
kworker/0:2       F    root     __         0.01 secs Tue Apr 19 04:47
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:47
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:42
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:41
kworker/3:3       F    root     __         0.00 secs Tue Apr 19 03:49
kworker/7:3       F    root     __         0.00 secs Tue Apr 19 04:46
kworker/7:0       F    root     __         0.00 secs Tue Apr 19 04:46
kworker/6:3       F    root     __         0.00 secs Tue Apr 19 04:42
kworker/6:1       F    root     __         0.00 secs Tue Apr 19 04:42
kworker/0:2       F    root     __         0.00 secs Tue Apr 19 04:37
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:35
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 04:44
kworker/0:0       F    root     __         0.01 secs Tue Apr 19 04:32
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:30
kworker/0:2       F    root     __         0.68 secs Tue Apr 19 01:40
sh                     goscuter __         0.00 secs Tue Apr 19 04:36
sh                     goscuter __         0.00 secs Tue Apr 19 04:36
paperconf              goscuter __         0.00 secs Tue Apr 19 04:36
libreoffice            goscuter __         0.00 secs Tue Apr 19 04:36
soffice                goscuter __         0.00 secs Tue Apr 19 04:36
oosplash.bin         X goscuter __         0.01 secs Tue Apr 19 04:36
uname                  goscuter __         0.00 secs Tue Apr 19 04:36
javaldx                goscuter __         0.01 secs Tue Apr 19 04:36
pagein                 goscuter __         0.04 secs Tue Apr 19 04:36
oosplash.bin           goscuter __         0.00 secs Tue Apr 19 04:36
uname                  goscuter __         0.00 secs Tue Apr 19 04:36
basename               goscuter __         0.00 secs Tue Apr 19 04:36
soffice           F    goscuter __         0.00 secs Tue Apr 19 04:36
dirname                goscuter __         0.00 secs Tue Apr 19 04:36
soffice           F    goscuter __         0.00 secs Tue Apr 19 04:36
stat                   goscuter __         0.00 secs Tue Apr 19 04:36
compiz            F    goscuter __         0.00 secs Tue Apr 19 04:36
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:25
gedit                  goscuter __         0.03 secs Tue Apr 19 04:33
nautilus          F    goscuter __         0.00 secs Tue Apr 19 04:33
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:33
lastcomm         S     root     pts/2      0.01 secs Tue Apr 19 04:33
kworker/7:3       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/3:1       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/7:0       F    root     __         0.00 secs Tue Apr 19 03:14
kworker/3:0       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:22
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:32
lastcomm         S     root     pts/2      0.01 secs Tue Apr 19 04:32
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:19
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:27
lastcomm         S     root     pts/2      0.01 secs Tue Apr 19 04:27
kworker/0:3       F    root     __         0.01 secs Tue Apr 19 04:17
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:25
ps                     goscuter pts/2      0.01 secs Tue Apr 19 04:25
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:25
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:25
ps               S     root     pts/2      0.03 secs Tue Apr 19 04:25
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:17
powertop         S     root     pts/2      0.50 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:14
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:12
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
xrandr           S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
iwpriv                 root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.03 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.06 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
modprobe               root     pts/2      0.00 secs Tue Apr 19 04:17
apt-check              goscuter __         0.45 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
lsb_release            goscuter __         0.02 secs Tue Apr 19 04:17
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:17
apt-get          S     root     pts/2      0.34 secs Tue Apr 19 04:17
apt-get           F    root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
touch                  root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/0      0.07 secs Tue Apr 19 04:17
dpkg             S     root     pts/0      0.25 secs Tue Apr 19 04:17
frontend               root     pts/0      0.16 secs Tue Apr 19 04:17
man-db.postinst        root     pts/0      0.00 secs Tue Apr 19 04:17
mandb            S     man      pts/0      0.04 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
man-db.config          root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/0      0.00 secs Tue Apr 19 04:17
stty                   root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/0      0.00 secs Tue Apr 19 04:17
stty                   root     pts/0      0.00 secs Tue Apr 19 04:17
locale                 root     pts/0      0.00 secs Tue Apr 19 04:17
rm                     root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb               root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb               root     pts/0      0.00 secs Tue Apr 19 04:17
tar                    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-split             root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg-preconfigu  S     root     pts/2      0.13 secs Tue Apr 19 04:17
dpkg-preconfigu   F    root     pts/2      0.00 secs Tue Apr 19 04:17
apt-extracttemp        root     pts/2      0.01 secs Tue Apr 19 04:17
gzip                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
stty                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
stty                   root     pts/2      0.00 secs Tue Apr 19 04:17
locale                 root     pts/2      0.00 secs Tue Apr 19 04:17
http                   root     pts/2      0.00 secs Tue Apr 19 04:17
http                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/0:3       F    root     __         0.00 secs Tue Apr 19 04:07
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:17
python                 goscuter pts/2      0.13 secs Tue Apr 19 04:17
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:17
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:17
python                 goscuter pts/2      0.14 secs Tue Apr 19 04:17
cron             SF    root     __         0.00 secs Tue Apr 19 04:17
sh               S     root     __         0.00 secs Tue Apr 19 04:17
run-parts              root     __         0.00 secs Tue Apr 19 04:17
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:16
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:16
ps                     goscuter pts/2      0.01 secs Tue Apr 19 04:16
uname                  goscuter pts/2      0.00 secs Tue Apr 19 04:15
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 04:14
kworker/6:3       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/6:1       F    root     __         0.00 secs Tue Apr 19 01:14
kworker/2:3       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/2:2       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:03
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:02
lastcomm               goscuter pts/2      0.00 secs Tue Apr 19 04:11
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:10
dir                    goscuter pts/2      0.00 secs Tue Apr 19 04:10
dir                    goscuter pts/2      0.00 secs Tue Apr 19 04:10
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:10
python                 goscuter pts/2      0.14 secs Tue Apr 19 04:10
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:09
info             S   X root     pts/2      0.01 secs Tue Apr 19 04:09
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:09
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:09
python                 goscuter pts/2      0.15 secs Tue Apr 19 04:09
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:09
tty              S     root     pts/2      0.00 secs Tue Apr 19 04:09
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:09
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:09
python                 goscuter pts/2      0.14 secs Tue Apr 19 04:09
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 03:58
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:08
python                 goscuter pts/2      0.12 secs Tue Apr 19 04:08
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:07
kill             S     root     pts/2      0.00 secs Tue Apr 19 04:07
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:07
kill             S     root     pts/2      0.00 secs Tue Apr 19 04:07
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:07
python                 goscuter pts/2      0.13 secs Tue Apr 19 04:07
kworker/0:3       F    root     __         0.00 secs Tue Apr 19 03:57
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:07
kill             S     root     pts/2      0.00 secs Tue Apr 19 04:07
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:06
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:06
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:05
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:05
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:05
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:05
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 03:52
uptime                 goscuter pts/2      0.00 secs Tue Apr 19 04:03
ac                     goscuter pts/2      0.00 secs Tue Apr 19 04:03
uptime                 goscuter pts/2      0.00 secs Tue Apr 19 04:03
ac                     goscuter pts/2      0.00 secs Tue Apr 19 04:02
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 03:52
ac                     goscuter pts/2      0.00 secs Tue Apr 19 04:02
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:01
ac               S     root     pts/2      0.00 secs Tue Apr 19 04:01
apt-check              goscuter __         0.47 secs Tue Apr 19 04:01
sh                     goscuter __         0.00 secs Tue Apr 19 04:01
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:01
sh                     goscuter __         0.00 secs Tue Apr 19 04:01
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:01
sh                     goscuter __         0.00 secs Tue Apr 19 04:01
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:01
sh                     goscuter __         0.00 secs Tue Apr 19 04:01
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:01
lsb_release            goscuter __         0.02 secs Tue Apr 19 04:01
ac                     goscuter pts/2      0.00 secs Tue Apr 19 04:00
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:00
apt-get          S     root     pts/2      0.26 secs Tue Apr 19 04:00
apt-get           F    root     pts/2      0.00 secs Tue Apr 19 04:00
sh                     root     pts/2      0.00 secs Tue Apr 19 04:00
touch                  root     pts/2      0.00 secs Tue Apr 19 04:00
dpkg             S     root     pts/0      0.08 secs Tue Apr 19 04:00
acct.postinst          root     pts/0      0.00 secs Tue Apr 19 04:00
invoke-rc.d            root     pts/0      0.00 secs Tue Apr 19 04:00
acct                   root     pts/0      0.00 secs Tue Apr 19 04:00
accton           S     root     pts/0      0.00 secs Tue Apr 19 04:00

```Seriously? So much nonsense. I had a really good feeling about the mistaken ~$ halt when my PC started going crazy with scripts whilst it was rebooting. Only to see a psuedo me is tying out commands on a terminal that isn't on my computer (I just flicked back manually through my commands - they match what I said above. 

halt
last
last
last
sudo last
last 

That's my commands. lol. Seems like I have a problem, that should be easily answered. But that has not been my experience, in the last 2 months. fml  

I like ubuntu and people on this forum seem cool, but for answers to stuff, where can I get them? I'm not a freeloader, I have $. 

So far, every Linux 'expert' I've paid has been an insulting, patronising, LYING moron. I got a champion guy on Launchpad helping me now and he's the first person who's expressly assisted in 2 months who seems like he has an IQ over 100. [I]Note: Maybe 80 have expressly assisted, many of them paid. 
[/I] 
Anyone know where I can find someone who **REALLY **actually knows Linux? I mean, we're talking open source code here right? :confused:

---

### Post by NightwishFan on 2011-04-18
Hmm.. You have no one specific issue in this thread you want resolved. Trying to reply here would degrade to be very confusing and unorganized. This also sounds more like a rant than anything. Also I fail to see what an individual's IQ or lack thereof has to do with the matter.

---

### Post by CharlesA on 2011-04-18
I would suggest making a thread for each issue. Also, watch the tone, being rude or condescending is a good way to get a thread locked.

---

### Post by Locke_99GS on 2011-04-18
> I have no desire for Virtual consoles, so why do I have recursive X11 nonsense going on? 

Because there is a symlink in the X11 folder to itself. These are not virtual consoles.

> Speaking of which, why do I have X11 at all? I'm quite fond of Gnome/Nautilus, at least when it's not crashing randomly. 

X11 is not your desktop environment, rather it is the mechanism which draws the desktop environment for you. It is the graphical back-end to pretty much everything. GNOME/KDE/LXDE/whatever run on *top* of X.

Nautilus is your graphical file manager.

> Why is there two of me logged in right now? Why do I keep jumping around from pts to pts and tty to tty? 

Every process is ran by a user, and with that users credentials. Many processes have their own account as a security measure. Any task ran by you, or your account on your behalf (such as running X, gdm, nautilus, and all the other things that must be ran as your but you don't actually start yourself) will show up as being executed by you... because you did - even if you didn't realize it. 

Everything on Linux runs in the terminal. Everything you see and use is just a graphical front-end for commands being run in a pts. Even when you open a terminal in GNOME, thats not the REAL terminal, only a terminal emulator - another program that runs inside of another shell.


It seems to me that the core of your Linux problems may be a lack of understanding of the fundamental methodologies of *nix computing.

Also, asking too many questions at once is a bit of a put-off to the rest of us. :) Perhaps one or two related questions at a time, next time? :)

---

### Post by sffvba[e0rt on 2011-04-18
Have you tried turning it off and on again?

---

### Post by wep940 on 2011-04-18
Also, keep in mind that if you do something in the terminal window, like ls -al | less, and then  use cntrl/z to terminate it, you leave that process running even though you aren't using it.  Everything you do can use other processes which will run in your userid.
 
I second the following:
 
[LIST]
[*]- get the fundamental basics first
[*]- break things up to one question per post and be CLEAR about the problem
[*]- being rude, belittling the people here, is a SURE way to NEVER get a response.  There are some extremely knowledgable people here.
[/LIST]I would also add the following:  take a chill pill, don't insult us about your "genious" and us being stupid - you might very well be surprised at people here are actually true geniouses.  As an example, if you were such a genious, you would have found the answers to your questions by using the CORRECT search phrases on the net.
 
You've insulted a lot of us, and don't let bean counts fool you.

---

### Post by frup on 2011-04-18
You could always pay for support,you know, instead of expecting others to help you for free when they do it out of their good will.

Generally if you're having problems you can't fix, it's worth backing up your data and seeing if a reinstall helps fix the problem.

---

### Post by Paqman on 2011-04-18
Stackexchange is a good place to ask very specific technical questions. They even have a specific Ubuntu site at [askubuntu.com](askubuntu.com).

---

### Post by ikt on 2011-04-18
> I like ubuntu and people on this forum seem cool, but for answers to stuff, where can I get them? I'm not a freeloader, I have $.

[http://shop.canonical.com/product_info.php?products_id=715](http://shop.canonical.com/product_info.php?products_id=715)

---

### Post by Quackers on 2011-04-18
I think maybe you worry too much :wink:

---

### Post by wojox on 2011-04-18
26 hours in a day. That's classic. You have much to learn young grasshopper. :P

---

### Post by goscuter1 on 2011-04-19
lol just quickly, I screwed up a gif posted it as an png that would have made no sense. Apologies. It was a humourous gif - actually one of the greatest gifs ever, in fact. 

> **NightwishFan said:**
> Hmm.. You have no one specific issue in this thread you want resolved. Trying to reply here would degrade to be very confusing and unorganized. This also sounds more like a rant than anything. Also I fail to see what an individual's IQ or lack thereof has to do with the matter.

Thank you for your clarifying and organised contribution. 

I would explain the link between IQ (flawed measuring tool that it is) and intelligence, but I fear I simply wouldn't be able to illuminate that link...adequately.  

> **CharlesA said:**
> I would suggest making a thread for each issue. Also, watch the tone, being rude or condescending is a good way to get a thread locked.

I'm cannot see where my tone got out of line? Can you point out specifics please, perhaps there was a misinterpretation on behalf of the reader? Without specifics, it's very hard to know, isn't it. 

As for rudeness, I have to strongly assert that no such rudeness existed. And respectfully add that I, personally, am mildly offended by the implication (again, without specifics) that I was rude, in any way. Can you please point out where you believed I was being rude, and your justifications for why you believed I was being rude in that instance?

As for condescension...it's more like valid frustration, really. Not condescension. Condescending is what I just was, to the rude poster who didn't see what IQ had to do with answers to questions. nb. my condescending tone there is IN RESPONSE to his unwarranted and unprovoked rudeness; specifically, his claim that he was prevented from answering a single question as to do so would be degrading.
[I]
nb. Please note my use of specifics, so as to avoid confusion and misinterpretation. Without specifics, all sorts of wild assertions can be made freely, without the chance of the accused to defend themselves or assess the allegations for any validity. [/I]

> **Locke_99GS said:**
> Because there is a symlink in the X11 folder to itself. These are not virtual consoles.

Actually, I was talking about my tty7 logins. And the logins that have no tty listed. 

And, whilst we're talking about TTYs....

[IMG]http://i.imgur.com/aPYaSl.jpg[/IMG]

Obviously I cannot access all those locked ones. 

> X11 is not your desktop environment, rather it is the mechaeveryonenism which draws the desktop environment for you. It is the graphical back-end to pretty much everything. GNOME/KDE/LXDE/whatever run on *top* of X.

Ah okay, thanks. You might have clarified something for me...I'm still pretty confused though. Because I was wrong, it wasn't recursion going on. I went all the way to the end. So I just have a heck of a lot of desktop-environments to go with all those TTYs?

Of course, everyone (including me) should have noticed that the **files** in the screenshot I posted were not symbolic links. Those are actual files, repeated in every one of the 30 or w/e X11 folders. The clue (which I also missed) is in the little arrow on some, and not on others.  You can take another look, or here is another image of the "end" of the X11 chain. What that [ executable is, I wouldn't mind knowing.

[http://i.imgur.com/tJemy.png](http://i.imgur.com/tJemy.png)

> Every process is ran by a user, and with that users credentials. 

```
cat                    goscuter __         0.00 secs Tue Apr 19 06:03 which                  goscuter __         0.00 secs Tue Apr 19 06:03 [compiz]("http://en.wikipedia.org/wiki/Compiz")            F    goscuter __         0.00 secs Tue Apr 19 06:03 **last                   goscuter pts/0      0.00 secs Tue Apr 19 06:02 last                   goscuter pts/0      0.00 secs Tue Apr 19 06:01 last                   goscuter pts/0      0.00 secs Tue Apr 19 06:01**
```

Where did I jump to, from pts/0, to make these 3 last commands? 


> It seems to me that the core of your Linux problems may be a lack of understanding of the fundamental methodologies of *nix computing.

I thank you for your contribution, pending clarifications. I'd also thank you not to patronise, please. My illiteracy with computers was 100% 9 weeks ago. I have been forced to learn fast. You also didn't answer the tougher questions, which came before and after the one you completely missed (X11 folder files not being symbolic links). Let's work together, rather than patronise - especially when not in the position to do so. 

> Also, asking too many questions at once is a bit of a put-off to the rest of us. Perhaps one or two related questions at a time, next time?

Can you please justify the logical validity of your request? Why everyonewould 500 threads (and I do have way more than 500 valid questions) make more sense than a single thread where they are all ordered logically? 

Each one of my questions is related. And if they aren't, it is merely a result of my ignorance. Which I'm working on, but it's tricky when questions are conveniently avoided - which it seems, the convenience of 500 threads instead of 1, might not be the reason for the request? I'll await that logical justification incoming, with a preemptive apology if you have one incoming.  

> **not found said:**
> Have you tried turning it off and on again?

Yes. Note the part where I said I learned about ~$ sudo halt

*nb. That kills all processes and reboots your computer. *

> **wep940 said:**
> Also, keep in mind that if you do something in the terminal window, like ls -al | less, and then  use cntrl/z to terminate it, you leave that process running even though you aren't using it.  Everything you do can use other processes which will run in your userid.

Which is a very good question, I think. Why are so many services loaded by default? And why do they all remain running, using up system resources even though the process has been terminated? I thought the entire point of Linux was streamlined for requirements, not bloated for exploitability - right?
 
> I second the following:
 
[LIST]
[*]- get the fundamental basics first
[*]- break things up to one question per post and be CLEAR about the problem
[*]- being rude, belittling the people here, is a SURE way to NEVER get a response.  There are some extremely knowledgable people here.
[*]I would also add the following:  take a chill pill, don't insult us  about your "genious" and us being stupid - you might very well be  surprised at people here are actually true geniouses.  As an example, if  you were such a genious, you would have found the answers to your  questions by using the CORRECT search phrases on the net.
[*]You've insulted a lot of us
[/LIST]


Please refer to my polite response above. 


[LIST]
[*]Patronising is very rude, especially when it is not warranted.
[*]Please don't request that I do illogical things, without providing a justification for your request. I await your justification for why 500 threads would be better than 1 thread with 500 questions.
[*]I resent your implication that I was unclear. I made my questions very clear. You didn't answer a single one of them, except for only one which raises even more valid questions.
[*]Again, I'm going to have to emphasise that without specifics, I cannot accept your allegations of rudeness without grave offence. Can you please provide those specifics, Sir?
[*]No doubt there are extremely knowledgeable people here. I have conversed with some of them, albeit in other threads. That makes my concerns regarding the lack of available answers, even more valid. There are COUNTLESS threads like this, all over this forum: [http://ubuntuforums.org/showthread.php?t=88490](http://ubuntuforums.org/showthread.php?t=88490)
I run into non-answered threads, far FAR more often than answered ones.
[*]Sir, again I will have to express my position that for you to misinterpret my self-deprecation incorrectly, and then launch an unwarranted attack, would offend most people. I am only offended by those who misspell genius, when denigrating a self-deprecating genius, in a world of browser spell-checkers which negate the requirement for any genius! *nb. just joking, I realise English is not everyone's first language. And spelling is lol, who cares. *
[*]But I assure you that the answers are not out there.  I just run into endless non-answered threads [http://ubuntuforums.org/showthread.php?t=1475554](http://ubuntuforums.org/showthread.php?t=1475554), or man pages that don't address the vulnerabilities or don't' explain why they are defaulted onto me when I have no use for them. I do find other people share my concerns about the security exploits they represent: [http://secunia.com/advisories/44124](http://secunia.com/advisories/44124)
[*]Only offensive people get offended, Sir. I assure you that your offence which you control, and which resulted from your misinterpretation, offends me 11 X as much! If you cannot see the point I'm making, you might want to read up on escalated offence, and what it can result in (when everyone decides what offends them and what doesn't).
[/LIST]
  
> **frup said:**
> You could always pay for support,you know, instead of expecting others to help you for free when they do it out of their good will.

I would be perfectly within my rights to be very rude in response to this. But I shall take the high road. Please read my post again, or even the quote below. 

> **ikt said:**
> >  	 		 			 				I like ubuntu and people on this forum seem cool, but for answers to  stuff, where can I get them? I'm not a freeloader, I have $.

[http://shop.canonical.com/product_info.php?products_id=715](http://shop.canonical.com/product_info.php?products_id=715)

GOD! Thank you! Is this incredibly new? It must be, I was searching high and low for this a week ago...

---

### Post by drs305 on 2011-04-19
> **goscuter1 said:**
> 
I would be perfectly within my rights to be very rude in response to this. But I shall take the high road. Please read my post again, or even the quote below. 

We will appreciate you taking the high road. And in fact you would *not* be within your rights to be rude. The Forum Code of Conduct expressly prohibits it.

We try as best we can to keep the Ubuntu forums a positive experience for all visitors. 

This thread is in a support forum and is being monitored by the staff; **everyone** please stick to the technical issues or the thread will be closed.

Added: I've also removed the video image from your post. The Code of Conduct addresses the use of images in posts.

---

### Post by goscuter1 on 2011-04-19
Crap sorry about the huge image Charles, I'm a moran - I certainly intended to make it a URL, but that was double-retardation because I could just paste the link for that...my bad. 

> **Quackers said:**
> I think maybe you worry too much :wink:

That's what a lot of people said when I was saying my Windows was being hacked 2 months ago. I've since proved it in ways Microsoft haven't even patched yet. Even though I reported the vulnerability with the evidence 2 months ago directly to them. I made a post about it on this forum actually: [http://ubuntuforums.org/showpost.php?p=10685576&postcount=102](http://ubuntuforums.org/showpost.php?p=10685576&postcount=102)

Of course, that's only maybe 2% of the supporting evidence. 

No doubt Microsoft will eventually release a patch with one of their lying claims about having never been notified prior. 

But in the meantime, 2 of my 3 systems are completely dead. And this one is full of questions that I'm about to get some answers to, thanks to the gentleman who provided me with a link to the Canonical home user support - woot. 

> **wojox said:**
> 26 hours in a day. That's classic. You have much to learn young grasshopper. :P

lolz. I assure you that I do. But whilst I realise you might be posting jovially, I've been stressed by all the rude allegations (unsupported) of my non-existent rudeness, so I apologise for pointing out you haven't actually contributed to that education I require. :p

---

### Post by Legeril on 2011-04-19
> I would explain the link between IQ (flawed measuring tool that it is)  and intelligence, but I fear I simply wouldn't be able to illuminate  that link...adequately.  

Stopped reading there, but I agree

---

### Post by goscuter1 on 2011-04-19
> **drs305 said:**
> We will appreciate you taking the high road. And in fact you would *not* be within your rights to be rude. The Forum Code of Conduct expressly prohibits it.

I generally try to. And am forced to do so often. But surely you will concede the fact there is no graver offence, than an attempted insult along the lines of:

> I like ubuntu and people on this forum seem cool, but  for answers to  stuff, where can I get them? **I'm not a freeloader, I  have $.** 			 		

*> You  could always pay for support,you know, instead of expecting others to  help you for free when they do it out of their good will.*
 			 		 	 	 
I mean, how rude must one be, before the Code of Conduct is enforced. But I shall forgive him, for they know not what they do. Quite literally, snicker. 

--------

More soberly however, is every thread on the forum monitored by support? That frightens me even more, because that means even more knowledgeable people don't have the answers to STACKS and STACKS of what appear to be pretty valid questions....

I mean, like this thread for example: [http://ubuntuforums.org/showthread.php?t=1663574](http://ubuntuforums.org/showthread.php?t=1663574)

If support staff have read that, there is a real problem here which makes it far more serious than an obscure bug - if no one knows the answer, right? 

```
**root@j-d:/home/goscuter1# locate samba**
/etc/samba
/etc/apparmor.d/abstractions/samba
/etc/bash_completion.d/samba
/etc/dhcp/dhclient-enter-hooks.d/samba
/etc/dhcp3/dhclient-enter-hooks.d/samba
/etc/pam.d/samba
/etc/samba/gdbcommands
/etc/samba/smb.conf
/usr/bin/net.samba3
/usr/bin/nmblookup.samba3
/usr/bin/testparm.samba3
/usr/lib/samba
/usr/lib/samba/idmap
/usr/lib/samba/nss_info
/usr/lib/samba/idmap/ad.so
/usr/lib/samba/idmap/adex.so
/usr/lib/samba/idmap/hash.so
/usr/lib/samba/idmap/ldap.so
/usr/lib/samba/idmap/rid.so
/usr/lib/samba/idmap/tdb2.so
/usr/lib/samba/nss_info/rfc2307.so
/usr/lib/samba/nss_info/sfu.so
/usr/lib/samba/nss_info/sfu20.so
/usr/share/samba
/usr/share/app-install/desktop/gadmin-samba.desktop
/usr/share/app-install/desktop/system-config-samba.desktop
/usr/share/app-install/icons/gadmin-samba.xpm
/usr/share/app-install/icons/system-config-samba.png
/usr/share/apport/package-hooks/source_samba.py
/usr/share/cups/templates/samba-export.tmpl
/usr/share/cups/templates/samba-exported.tmpl
/usr/share/cups/templates/de/samba-export.tmpl
/usr/share/cups/templates/de/samba-exported.tmpl
/usr/share/cups/templates/es/samba-export.tmpl
/usr/share/cups/templates/es/samba-exported.tmpl
/usr/share/cups/templates/eu/samba-export.tmpl
/usr/share/cups/templates/eu/samba-exported.tmpl
/usr/share/cups/templates/id/samba-export.tmpl
/usr/share/cups/templates/id/samba-exported.tmpl
/usr/share/cups/templates/it/samba-export.tmpl
/usr/share/cups/templates/it/samba-exported.tmpl
/usr/share/cups/templates/ja/samba-export.tmpl
/usr/share/cups/templates/ja/samba-exported.tmpl
/usr/share/cups/templates/pl/samba-export.tmpl
/usr/share/cups/templates/pl/samba-exported.tmpl
/usr/share/cups/templates/ru/samba-export.tmpl
/usr/share/cups/templates/ru/samba-exported.tmpl
/usr/share/doc/samba-common
/usr/share/doc/samba-common-bin
/usr/share/doc/cups/examples/samba-postscript.convs
/usr/share/doc/cups/examples/samba-postscript.types
/usr/share/doc/cups/examples/samba-to-ps
/usr/share/doc/samba-common/NEWS.Debian.gz
/usr/share/doc/samba-common/README.build.gz
/usr/share/doc/samba-common/README.gz
/usr/share/doc/samba-common/Roadmap
/usr/share/doc/samba-common/WHATSNEW.txt.gz
/usr/share/doc/samba-common/changelog.Debian.gz
/usr/share/doc/samba-common/copyright
/usr/share/doc/samba-common-bin/NEWS.Debian.gz
/usr/share/doc/samba-common-bin/README.build.gz
/usr/share/doc/samba-common-bin/changelog.Debian.gz
/usr/share/doc/samba-common-bin/copyright
/usr/share/icons/Humanity/devices/24/samba.svg
/usr/share/icons/Humanity/devices/48/samba.svg
/usr/share/man/man1/nmblookup.samba3.1.gz
/usr/share/man/man1/testparm.samba3.1.gz
/usr/share/man/man7/samba.7.gz
/usr/share/man/man8/net.samba3.8.gz
/usr/share/samba/lowcase.dat
/usr/share/samba/panic-action
/usr/share/samba/smb.conf
/usr/share/samba/upcase.dat
/usr/share/samba/valid.dat
/usr/src/linux-headers-2.6.38-8-generic-pae/include/config/usb/serial/samba.h
/var/cache/samba
/var/cache/samba/netsamlogon_cache.tdb
/var/cache/samba/winbindd_cache.tdb
/var/lib/samba
/var/lib/dpkg/info/samba-common-bin.list
/var/lib/dpkg/info/samba-common-bin.md5sums
/var/lib/dpkg/info/samba-common-bin.postinst
/var/lib/dpkg/info/samba-common-bin.prerm
/var/lib/dpkg/info/samba-common.conffiles
/var/lib/dpkg/info/samba-common.config
/var/lib/dpkg/info/samba-common.list
/var/lib/dpkg/info/samba-common.md5sums
/var/lib/dpkg/info/samba-common.postinst
/var/lib/dpkg/info/samba-common.postrm
/var/lib/dpkg/info/samba-common.templates
/var/lib/samba/secrets.tdb
/var/lib/ucf/cache/:etc:samba:smb.conf
/var/log/samba
/var/log/samba/cores
/var/log/samba/log.wb-J-D
/var/log/samba/log.winbindd
/var/log/samba/cores/winbindd
**root@j-d:/home/goscuter1# sudo apt-get remove samba**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
**root@j-d:/home/goscuter1# samba**
The program 'samba' is currently not installed.  You can install it by typing:
apt-get install samba4

```

And inside the config files is where it gets extremely disturbing. Because non-default values are set, on the wrong side of "secure". 

Hmm. I love Gnome window docks so much. But...if ubuntu is just going to be another bloated ship like Windows (and I'm not saying it is, merely that I haven't found the answers yet)...what would be the point? 

Man but I do love the 4 sidebar window docks. sigh.

---

### Post by NightwishFan on 2011-04-19
Nevermind, is not really on topic. Apologies.

---

### Post by goscuter1 on 2011-04-19
I guess I really should be asking Canonical (and I will) but just for public interest, I have a boot image I just found, which DBAN and KillDisk low-level formatting aren't removing. 

Contents of my /var/log/Xorg.0.log (I also have an Xorg.0.log.old - which I cannot access, which happens to be the case for a massive amount of files I really would like to access, being the owner of them and all). 

```
[    16.424] 
X.Org X Server 1.10.0.902 (1.10.1 RC 2)
Release Date: 2011-04-08
[    16.424] X Protocol Version 11, Revision 0
[    16.424] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    16.424] Current Operating System: Linux j-d 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
[    16.424] Kernel command line: **BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=b511f6e9-75d8-425f-9b14-fb6d269f7fdf ro quiet splash vt.handoff=7**
[    16.424] Build Date: 11 April 2011  07:04:59AM
[    16.424] xorg-server 2:1.10.0.902-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    16.424] Current version of pixman: 0.20.2
[    16.424]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    16.424] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.424] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 19 09:53:22 2011
[COLOR=Black][    16.424] (==) Using config file: "/etc/X11/xorg.conf"[/COLOR]
[COLOR=Red][    16.424] (==) Using system config directory "/usr/share/X11/xorg.conf.d"[/COLOR]
[    16.425] (==) No Layout section.  Using the first Screen section.
[    16.425] (**) |-->Screen "Default Screen" (0)
[    16.425] (**) |   |-->Monitor "<default monitor>"
[    16.425] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    16.425] (==) Automatically adding devices
[    16.425] (==) Automatically enabling devices
[    16.425] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.425]     Entry deleted from font path.
[    16.425] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.425]     Entry deleted from font path.
[    16.425] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.425]     Entry deleted from font path.
[    16.425] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.425]     Entry deleted from font path.
[    16.425] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.425]     Entry deleted from font path.
[    16.425] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    16.425] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.425] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.425] (II) Loader magic: 0x81ffde0
[    16.425] (II) Module ABI versions:
[    16.425]     X.Org ANSI C Emulation: 0.4
[    16.425]     X.Org Video Driver: 10.0
[    16.425]     X.Org XInput driver : 12.3
[    16.425]     X.Org Server Extension : 5.0
[    16.426] (--) PCI:*(0:2:0:0) 1002:689e:1787:200a rev 0, Mem @ 0xd0000000/268435456, 0xfbbc0000/131072, I/O @ 0x0000b000/256, BIOS @ 0x????????/131072
[    16.426] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.426] (II) "extmod" will be loaded by default.
[    16.426] (II) "dbe" will be loaded by default.
[    16.426] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    16.426] (II) "record" will be loaded by default.
[    16.426] (II) "dri" will be loaded by default.
[    16.426] (II) "dri2" will be loaded by default.
[    16.426] (II) LoadModule: "glx"
[    16.426] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    16.426] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    16.426]     compiled for 6.9.0, module version = 1.0.0
[    16.426] (II) Loading extension GLX
[    16.426] (II) LoadModule: "extmod"
[    16.442] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.442] (II) Module extmod: vendor="X.Org Foundation"
[    16.442]     compiled for 1.10.0.902, module version = 1.0.0
[    16.442]     Module class: X.Org Server Extension
[    16.442]     ABI class: X.Org Server Extension, version 5.0
[    16.442] (II) Loading extension MIT-SCREEN-SAVER
[    16.442] (II) Loading extension XFree86-VidModeExtension
[    16.442] (II) Loading extension XFree86-DGA
[    16.442] (II) Loading extension DPMS
[    16.442] (II) Loading extension XVideo
[    16.442] (II) Loading extension XVideo-MotionCompensation
[    16.442] (II) Loading extension X-Resource
[    16.442] (II) LoadModule: "dbe"
[    16.442] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.442] (II) Module dbe: vendor="X.Org Foundation"
[    16.442]     compiled for 1.10.0.902, module version = 1.0.0
[    16.442]     Module class: X.Org Server Extension
[    16.442]     ABI class: X.Org Server Extension, version 5.0
[    16.442] (II) Loading extension DOUBLE-BUFFER
[    16.442] (II) LoadModule: "record"
[    16.442] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.442] (II) Module record: vendor="X.Org Foundation"
[    16.442]     compiled for 1.10.0.902, module version = 1.13.0
[    16.442]     Module class: X.Org Server Extension
[    16.442]     ABI class: X.Org Server Extension, version 5.0
[    16.442] (II) Loading extension RECORD
[    16.442] (II) LoadModule: "dri"
[    16.442] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.442] (II) Module dri: vendor="X.Org Foundation"
[    16.442]     compiled for 1.10.0.902, module version = 1.0.0
[    16.442]     ABI class: X.Org Server Extension, version 5.0
[    16.442] (II) Loading extension XFree86-DRI
[    16.442] (II) LoadModule: "dri2"
[    16.443] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.443] (II) Module dri2: vendor="X.Org Foundation"
[    16.443]     compiled for 1.10.0.902, module version = 1.2.0
[    16.443]     ABI class: X.Org Server Extension, version 5.0
[    16.443] (II) Loading extension DRI2
[    16.443] (==) Matched fglrx as autoconfigured driver 0
[    16.443] (==) Matched ati as autoconfigured driver 1
[    16.443] (==) Matched vesa as autoconfigured driver 2
[    16.443] (==) Matched fbdev as autoconfigured driver 3
[    16.443] (==) Assigned the driver to the xf86ConfigLayout
[    16.443] (II) LoadModule: "fglrx"
[    16.443] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.456] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    16.456]     compiled for 1.4.99.906, module version = 8.84.60
[    16.456]     Module class: X.Org Video Driver
[    16.456] (II) Loading sub module "fglrxdrm"
[    16.456] (II) LoadModule: "fglrxdrm"
[    16.457] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.457] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    16.457]     compiled for 1.4.99.906, module version = 8.84.60
[    16.457] (II) LoadModule: "ati"
[    16.457] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    16.457] (II) Module ati: vendor="X.Org Foundation"
[    16.457]     compiled for 1.10.0, module version = 6.14.0
[    16.457]     Module class: X.Org Video Driver
[    16.457]     ABI class: X.Org Video Driver, version 10.0
[    16.457] (II) LoadModule: "radeon"
[    16.457] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    16.457] (II) Module radeon: vendor="X.Org Foundation"
[    16.457]     compiled for 1.10.0, module version = 6.14.0
[    16.457]     Module class: X.Org Video Driver
[    16.457]     ABI class: X.Org Video Driver, version 10.0
[    16.457] (II) LoadModule: "vesa"
[    16.458] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.458] (II) Module vesa: vendor="X.Org Foundation"
[    16.458]     compiled for 1.10.0, module version = 2.3.0
[    16.458]     Module class: X.Org Video Driver
[    16.458]     ABI class: X.Org Video Driver, version 10.0
[    16.458] (II) LoadModule: "fbdev"
[    16.458] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.458] (II) Module fbdev: vendor="X.Org Foundation"
[    16.458]     compiled for 1.10.0, module version = 0.4.2
[    16.458]     ABI class: X.Org Video Driver, version 10.0
[    16.458] (II) ATI Proprietary Linux Driver Version Identifier:8.84.60
[    16.458] (II) ATI Proprietary Linux Driver Release Identifier: 8.84.6                               
[    16.458] (II) ATI Proprietary Linux Driver Build Date: Mar 24 2011 19:27:41
[    16.458] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS,
    Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS
[    16.462] (II) VESA: driver for VESA chipsets: vesa
[    16.462] (II) FBDEV: driver for framebuffer: fbdev
[    16.462] (++) using VT number 7

[    16.462] (WW) Falling back to old probe method for fglrx
[    16.469] (II) Loading PCS database from /etc/ati/amdpcsdb
[    16.470] (--) Assigning device section with no busID to primary device
[    16.470] (--) Chipset Supported AMD Graphics Processor (0x689E) found
[    16.470] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    16.470] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    16.470] (II) AMD Video driver is signed
[    16.470] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.470] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.470] (II) fglrx(0): pEnt->device->identifier=0x81ec9e8
[    16.470] (WW) Falling back to old probe method for vesa
[    16.470] (WW) Falling back to old probe method for fbdev
[    16.470] (II) Loading sub module "fbdevhw"
[    16.471] (II) LoadModule: "fbdevhw"
[    16.471] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.471] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.471]     compiled for 1.10.0.902, module version = 0.0.2
[    16.471]     ABI class: X.Org Video Driver, version 10.0
[    16.471] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    16.471] (II) Loading sub module "vgahw"
[    16.471] (II) LoadModule: "vgahw"
[    16.490] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    16.490] (II) Module vgahw: vendor="X.Org Foundation"
[    16.490]     compiled for 1.10.0.902, module version = 0.1.0
[    16.490]     ABI class: X.Org Video Driver, version 10.0
[    16.491] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    16.491] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    16.491] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    16.491] (==) fglrx(0): Default visual is TrueColor
[    16.491] (==) fglrx(0): RGB weight 888
[    16.491] (II) fglrx(0): Using 8 bits per RGB 
[    16.491] (==) fglrx(0): Buffer Tiling is ON
[    16.491] (II) Loading sub module "fglrxdrm"
[    16.491] (II) LoadModule: "fglrxdrm"
[    16.491] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    16.491] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    16.491]     compiled for 1.4.99.906, module version = 8.84.60
[    16.492] ukiDynamicMajor: found major device number 249
[    16.492] ukiDynamicMajor: found major device number 249
[    16.492] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    16.492] ukiOpenDevice: node name is /dev/ati/card0
[    16.492] ukiOpenDevice: open result is 11, (OK)
[    16.492] ukiOpenByBusid: ukiOpenMinor returns 11
[    16.493] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    16.493] (==) fglrx(0): NoAccel = NO
[    16.493] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    16.493] (--) fglrx(0): Chipset: "ATI Radeon HD 5800 Series  " (Chipset = 0x689e)
[    16.493] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x200a)
[    16.493] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    16.493] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    16.493] (--) fglrx(0): MMIO registers at 0xfbbc0000
[    16.493] (--) fglrx(0): I/O port at 0x0000b000
[    16.493] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    16.493] (II) fglrx(0): AC Adapter is used
[    16.496] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    16.496] (II) Loading sub module "vbe"
[    16.496] (II) LoadModule: "vbe"
[    16.497] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    16.497] (II) Module vbe: vendor="X.Org Foundation"
[    16.497]     compiled for 1.10.0.902, module version = 1.1.0
[    16.497]     ABI class: X.Org Video Driver, version 10.0
[    16.497] (II) fglrx(0): VESA BIOS detected
[    16.497] (II) fglrx(0): VESA VBE Version 3.0
[    16.497] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    16.497] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    16.497] (II) fglrx(0): VESA VBE OEM Software Rev: 12.20
[    16.497] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    16.497] (II) fglrx(0): VESA VBE OEM Product: R-00
[    16.497] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    16.536] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    16.536] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    16.536] (II) fglrx(0): PCIE card detected
[    16.536] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    16.536] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    16.538] (II) fglrx(0): Using adapter: 2:0.0.
[    16.569] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    16.869] (II) fglrx(0): Interrupt handler installed at IRQ 71.
[    16.869] (II) fglrx(0): RandR 1.2 support is enabled!
[    16.869] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    16.869] (==) fglrx(0): Center Mode is disabled 
[    16.869] (II) Loading sub module "fb"
[    16.869] (II) LoadModule: "fb"
[    16.869] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.869] (II) Module fb: vendor="X.Org Foundation"
[    16.869]     compiled for 1.10.0.902, module version = 1.0.0
[    16.869]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.869] (II) Loading sub module "ddc"
[    16.869] (II) LoadModule: "ddc"
[    16.869] (II) Module "ddc" already built-in
[    17.017] (II) fglrx(0): Finished Initialize PPLIB!
[    17.017] (II) fglrx(0): Output DFP1 has no monitor section
[    17.017] (II) fglrx(0): Output DFP2 has no monitor section
[    17.017] (II) fglrx(0): Output DFP3 has no monitor section
[    17.017] (II) fglrx(0): Output DFP4 has no monitor section
[    17.017] (II) fglrx(0): Output CRT1 has no monitor section
[    17.017] (II) fglrx(0): Output CRT2 has no monitor section
[    17.017] (II) Loading sub module "ddc"
[    17.017] (II) LoadModule: "ddc"
[    17.017] (II) Module "ddc" already built-in
[    17.017] (II) fglrx(0): Connected Display0: DFP4
[    17.017] (II) fglrx(0): Display0 EDID data ---------------------------
[    17.017] (II) fglrx(0): Manufacturer: NEC  Model: 678c  Serial#: 16843009
[    17.017] (II) fglrx(0): Year: 2010  Week: 37
[    17.017] (II) fglrx(0): EDID Version: 1.3
[    17.017] (II) fglrx(0): Digital Display Input
[    17.017] (II) fglrx(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    17.017] (II) fglrx(0): Gamma: 2.20
[    17.017] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    17.017] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.017] (II) fglrx(0): First detailed timing is preferred mode
[    17.017] (II) fglrx(0): redX: 0.644 redY: 0.335   greenX: 0.304 greenY: 0.613
[    17.017] (II) fglrx(0): blueX: 0.146 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    17.017] (II) fglrx(0): Supported established timings:
[    17.017] (II) fglrx(0): 720x400@70Hz
[    17.017] (II) fglrx(0): 640x480@60Hz
[    17.017] (II) fglrx(0): 640x480@67Hz
[    17.017] (II) fglrx(0): 640x480@72Hz
[    17.017] (II) fglrx(0): 640x480@75Hz
[    17.017] (II) fglrx(0): 800x600@56Hz
[    17.017] (II) fglrx(0): 800x600@60Hz
[    17.017] (II) fglrx(0): 800x600@72Hz
[    17.017] (II) fglrx(0): 800x600@75Hz
[    17.017] (II) fglrx(0): 832x624@75Hz
[    17.017] (II) fglrx(0): 1024x768@60Hz
[    17.017] (II) fglrx(0): 1024x768@70Hz
[    17.017] (II) fglrx(0): 1024x768@75Hz
[    17.017] (II) fglrx(0): 1280x1024@75Hz
[    17.017] (II) fglrx(0): 1152x864@75Hz
[    17.017] (II) fglrx(0): Manufacturer's mask: 0
[    17.017] (II) fglrx(0): Supported standard timings:
[    17.017] (II) fglrx(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    17.017] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    17.017] (II) fglrx(0): #2: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    17.017] (II) fglrx(0): #3: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    17.017] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    17.017] (II) fglrx(0): #5: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    17.017] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    17.017] (II) fglrx(0): #7: hsize: 1920  vsize 1200  refresh: 60  vid: 209
[    17.017] (II) fglrx(0): Supported detailed timing:
[    17.017] (II) fglrx(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
[    17.017] (II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    17.017] (II) fglrx(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[    17.017] (II) fglrx(0): Ranges: V min: 50 V max: 85 Hz, H min: 31 H max: 92 kHz, PixClock max 175 MHz
[    17.017] (II) fglrx(0): Monitor name: LCD2490WUXi2
[    17.017] (II) fglrx(0): Serial No: 09306795UA
[    17.017] (II) fglrx(0): EDID (in hex):
[    17.017] (II) fglrx(0):     00ffffffffffff0038a38c6701010101
[    17.017] (II) fglrx(0):     2514010380342078eafc85a4554d9d25
[    17.017] (II) fglrx(0):     125054bfef8081c0818090408bc09500
[    17.017] (II) fglrx(0):     a940b300d100283c80a070b023403020
[    17.017] (II) fglrx(0):     360006442100001a000000fd0032551f
[    17.017] (II) fglrx(0):     5c11000a202020202020000000fc004c
[    17.017] (II) fglrx(0):     43443234393057555869320a000000ff
[    17.018] (II) fglrx(0):     00303933303637393555410a2020003c
[    17.018] (II) fglrx(0): End of Display0 EDID data --------------------
[    17.039] (II) fglrx(0): EDID for output DFP1
[    17.039] (II) fglrx(0): EDID for output DFP2
[    17.039] (II) fglrx(0): EDID for output DFP3
[    17.039] (II) fglrx(0): EDID for output DFP4
[    17.039] (II) fglrx(0): Manufacturer: NEC  Model: 678c  Serial#: 16843009
[    17.039] (II) fglrx(0): Year: 2010  Week: 37
[    17.039] (II) fglrx(0): EDID Version: 1.3
[    17.039] (II) fglrx(0): Digital Display Input
[    17.039] (II) fglrx(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    17.039] (II) fglrx(0): Gamma: 2.20
[    17.039] (II) fglrx(0): DPMS capabilities: StandBy Suspend Off
[    17.039] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.039] (II) fglrx(0): First detailed timing is preferred mode
[    17.039] (II) fglrx(0): redX: 0.644 redY: 0.335   greenX: 0.304 greenY: 0.613
[    17.039] (II) fglrx(0): blueX: 0.146 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    17.039] (II) fglrx(0): Supported established timings:
[    17.039] (II) fglrx(0): 720x400@70Hz
[    17.039] (II) fglrx(0): 640x480@60Hz
[    17.039] (II) fglrx(0): 640x480@67Hz
[    17.039] (II) fglrx(0): 640x480@72Hz
[    17.039] (II) fglrx(0): 640x480@75Hz
[    17.039] (II) fglrx(0): 800x600@56Hz
[    17.039] (II) fglrx(0): 800x600@60Hz
[    17.039] (II) fglrx(0): 800x600@72Hz
[    17.039] (II) fglrx(0): 800x600@75Hz
[    17.039] (II) fglrx(0): 832x624@75Hz
[    17.039] (II) fglrx(0): 1024x768@60Hz
[    17.039] (II) fglrx(0): 1024x768@70Hz
[    17.039] (II) fglrx(0): 1024x768@75Hz
[    17.039] (II) fglrx(0): 1280x1024@75Hz
[    17.039] (II) fglrx(0): 1152x864@75Hz
[    17.039] (II) fglrx(0): Manufacturer's mask: 0
[    17.039] (II) fglrx(0): Supported standard timings:
[    17.039] (II) fglrx(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    17.039] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    17.039] (II) fglrx(0): #2: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    17.039] (II) fglrx(0): #3: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    17.039] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    17.039] (II) fglrx(0): #5: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    17.039] (II) fglrx(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    17.039] (II) fglrx(0): #7: hsize: 1920  vsize 1200  refresh: 60  vid: 209
[    17.039] (II) fglrx(0): Supported detailed timing:
[    17.039] (II) fglrx(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
[    17.039] (II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    17.039] (II) fglrx(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[    17.039] (II) fglrx(0): Ranges: V min: 50 V max: 85 Hz, H min: 31 H max: 92 kHz, PixClock max 175 MHz
[    17.039] (II) fglrx(0): Monitor name: LCD2490WUXi2
[    17.039] (II) fglrx(0): Serial No: 09306795UA
[    17.039] (II) fglrx(0): EDID (in hex):
[    17.039] (II) fglrx(0):     00000000782830293a20454449442028
[    17.039] (II) fglrx(0):     696e20686578293a0a006bb7f0336bb7
[    17.039] (II) fglrx(0):     125054bf410000000000000078283029
[    17.039] (II) fglrx(0):     3a2046697273742064657461696c6564
[    17.039] (II) fglrx(0):     2074696d696e67206973207072656665
[    17.039] (II) fglrx(0):     72726564206d6f64650a000a00fc004c
[    17.039] (II) fglrx(0):     43443234210000000000000078283029
[    17.039] (II) fglrx(0):     3a200925730a00733a2056206d696e3a
[    17.039] (II) fglrx(0): Printing probed modes for output DFP4
[    17.039] (II) fglrx(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1920x1080"x60.0  154.00  1920 1968 2000 2080  1080 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    17.039] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x800"x75.0  135.00  1280 1296 1440 1688  800 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x800"x60.0  108.00  1280 1328 1440 1688  800 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x768"x75.0  135.00  1280 1296 1440 1688  768 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1328 1440 1688  768 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    17.039] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.039] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    17.039] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.040] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    17.040] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.040] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.040] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.040] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.040] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz)
[    17.040] (II) fglrx(0): Modeline "640x480"x67.0   27.28  640 664 728 816  480 481 484 499 -hsync +vsync (33.4 kHz)
[    17.040] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.040] (II) fglrx(0): EDID for output CRT1
[    17.040] (II) fglrx(0): EDID for output CRT2
[    17.040] (II) fglrx(0): Output DFP1 disconnected
[    17.040] (II) fglrx(0): Output DFP2 disconnected
[    17.040] (II) fglrx(0): Output DFP3 disconnected
[    17.040] (II) fglrx(0): Output DFP4 connected
[    17.040] (II) fglrx(0): Output CRT1 disconnected
[    17.040] (II) fglrx(0): Output CRT2 disconnected
[    17.040] (II) fglrx(0): Using exact sizes for initial modes
[    17.040] (II) fglrx(0): Output DFP4 using initial mode 1920x1200
[    17.040] (II) fglrx(0): DPI set to (96, 96)
[    17.040] (II) fglrx(0): Eyefinity capable adapter detected.
[    17.040] (II) fglrx(0): Adapter ATI Radeon HD 5800 Series   has 3 configurable heads and 1 displays connected.
[    17.040] (==) fglrx(0):  PseudoColor visuals disabled
[    17.040] (II) Loading sub module "ramdac"
[    17.040] (II) LoadModule: "ramdac"
[    17.040] (II) Module "ramdac" already built-in
[    17.040] (==) fglrx(0): NoDRI = NO
[    17.040] (==) fglrx(0): Capabilities: 0x00000000
[    17.040] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    17.040] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    17.040] (==) fglrx(0): UseFastTLS=0
[    17.040] (==) fglrx(0): BlockSignalsOnLock=1
[    17.040] (II) UnloadModule: "radeon"
[    17.040] (II) Unloading radeon
[    17.040] (II) UnloadModule: "vesa"
[    17.040] (II) Unloading vesa
[    17.040] (II) UnloadModule: "fbdev"
[    17.040] (II) Unloading fbdev
[    17.040] (II) UnloadModule: "fbdevhw"
[    17.040] (II) Unloading fbdevhw
[    17.040] (--) Depth 24 pixmap format is 32 bpp
[    17.040] (II) Loading extension ATIFGLRXDRI
[    17.040] (II) fglrx(0): doing swlDriScreenInit
[    17.040] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    17.040] ukiDynamicMajor: found major device number 249
[    17.040] ukiDynamicMajor: found major device number 249
[    17.040] ukiDynamicMajor: found major device number 249
[    17.040] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    17.040] ukiOpenDevice: node name is /dev/ati/card0
[    17.040] ukiOpenDevice: open result is 16, (OK)
[    17.040] ukiOpenByBusid: ukiOpenMinor returns 16
[    17.040] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    17.040] (II) fglrx(0): [uki] DRM interface version 1.0
[    17.040] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:2:0:0"
[    17.040] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    17.040] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb6700000
[    17.040] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    17.040] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    17.040] (II) fglrx(0): swlDriScreenInit done
[    17.040] (II) fglrx(0): Kernel Module Version Information:
[    17.040] (II) fglrx(0):     Name: fglrx
[    17.040] (II) fglrx(0):     Version: 8.84.60
[    17.040] (II) fglrx(0):     Date: Mar 24 2011
[    17.040] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    17.040] (II) fglrx(0): Kernel Module version matches driver.
[    17.040] (II) fglrx(0): Kernel Module Build Time Information:
[    17.040] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-8-generic-pae
[    17.040] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    17.041] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    17.041] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    17.041] (II) fglrx(0): [uki] register handle = 0x00004000
[    17.055] (II) fglrx(0): DRI initialization successfull
[    17.055] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x010e0000
[    17.055] (==) fglrx(0): Backing store disabled
[    17.055] (II) Loading extension FGLRXEXTENSION
[    17.055] (==) fglrx(0): DPMS enabled
[    17.055] (II) fglrx(0): Initialized in-driver Xinerama extension
[    17.055] (**) fglrx(0): Textured Video is enabled.
[    17.055] (II) LoadModule: "glesx"
[    17.055] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    17.056] (II) Module glesx: vendor="X.Org Foundation"
[    17.056]     compiled for 1.4.99.906, module version = 1.0.0
[    17.056] (II) Loading extension GLESX
[    17.056] (II) fglrx(0): GLESX enableFlags = 592
[    17.056] (II) fglrx(0): GLESX is enabled
[    17.056] (II) LoadModule: "amdxmm"
[    17.056] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    17.057] (II) Module amdxmm: vendor="X.Org Foundation"
[    17.057]     compiled for 1.4.99.906, module version = 2.0.0
[    17.123] (II) Loading extension AMDXVOPL
[    17.123] (II) Loading extension AMDXVBA
[    17.124] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    17.125] (II) fglrx(0): Enable composite support successfully
[    17.125] (II) fglrx(0): X context handle = 0x1
[    17.125] (II) fglrx(0): [DRI] installation complete
[    17.125] (==) fglrx(0): Silken mouse enabled
[    17.126] (==) fglrx(0): Using HW cursor of display infrastructure!
[    17.126] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    17.744] (--) RandR disabled
[    17.744] (II) Initializing built-in extension Generic Event Extension
[    17.744] (II) Initializing built-in extension SHAPE
[    17.744] (II) Initializing built-in extension MIT-SHM
[    17.744] (II) Initializing built-in extension XInputExtension
[    17.744] (II) Initializing built-in extension XTEST
[    17.744] (II) Initializing built-in extension BIG-REQUESTS
[    17.744] (II) Initializing built-in extension SYNC
[    17.744] (II) Initializing built-in extension XKEYBOARD
[    17.744] (II) Initializing built-in extension XC-MISC
[    17.744] (II) Initializing built-in extension SECURITY
[    17.744] (II) Initializing built-in extension XINERAMA
[    17.744] (II) Initializing built-in extension XFIXES
[    17.744] (II) Initializing built-in extension RENDER
[    17.744] (II) Initializing built-in extension RANDR
[    17.744] (II) Initializing built-in extension COMPOSITE
[    17.744] (II) Initializing built-in extension DAMAGE
[    17.744] (II) Initializing built-in extension GESTURE
[    17.762] ukiDynamicMajor: found major device number 249
[    17.762] ukiDynamicMajor: found major device number 249
[    17.762] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    17.762] ukiOpenDevice: node name is /dev/ati/card0
[    17.762] ukiOpenDevice: open result is 18, (OK)
[    17.762] ukiOpenByBusid: ukiOpenMinor returns 18
[    17.762] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    17.827] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    17.827] (II) fglrx(0): Enable the clock gating!
[    17.827] (II) fglrx(0): Setting screen physical size to 507 x 317
[    17.835] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.841] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.841] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.841] (II) LoadModule: "evdev"
[    17.842] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.842] (II) Module evdev: vendor="X.Org Foundation"
[    17.842]     compiled for 1.10.0.902, module version = 2.6.0
[    17.842]     Module class: X.Org XInput Driver
[    17.842]     ABI class: X.Org XInput driver, version 12.3
[    17.842] (II) Using input driver 'evdev' for 'Power Button'
[    17.842] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.842] (**) Power Button: always reports core events
[    17.842] (**) Power Button: Device: "/dev/input/event1"
[    17.842] (--) Power Button: Found keys
[    17.842] (II) Power Button: Configuring as keyboard
[    17.842] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    17.842] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.842] (**) Option "xkb_rules" "evdev"
[    17.842] (**) Option "xkb_model" "pc105"
[    17.842] (**) Option "xkb_layout" "us"
[    17.844] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.844] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.844] (II) Using input driver 'evdev' for 'Power Button'
[    17.844] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.844] (**) Power Button: always reports core events
[    17.844] (**) Power Button: Device: "/dev/input/event0"
[    17.845] (--) Power Button: Found keys
[    17.845] (II) Power Button: Configuring as keyboard
[    17.845] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    17.845] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.845] (**) Option "xkb_rules" "evdev"
[    17.845] (**) Option "xkb_model" "pc105"
[    17.845] (**) Option "xkb_layout" "us"
[    17.848] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    17.848] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    17.848] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    17.848] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.849] (**) Logitech USB Receiver: always reports core events
[    17.849] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    17.849] (--) Logitech USB Receiver: Found keys
[    17.849] (II) Logitech USB Receiver: Configuring as keyboard
[    17.849] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input3/event3"
[    17.849] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    17.849] (**) Option "xkb_rules" "evdev"
[    17.849] (**) Option "xkb_model" "pc105"
[    17.849] (**) Option "xkb_layout" "us"
[    17.849] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    17.849] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    17.849] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    17.849] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    17.849] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.849] (**) Logitech USB Receiver: always reports core events
[    17.849] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    17.849] (--) Logitech USB Receiver: Found 20 mouse buttons
[    17.849] (--) Logitech USB Receiver: Found scroll wheel(s)
[    17.849] (--) Logitech USB Receiver: Found relative axes
[    17.849] (--) Logitech USB Receiver: Found x and y relative axes
[    17.849] (--) Logitech USB Receiver: Found absolute axes
[    17.849] (II) evdev-grail: failed to open grail, no gesture support
[    17.849] (--) Logitech USB Receiver: Found keys
[    17.850] (II) Logitech USB Receiver: Configuring as mouse
[    17.850] (II) Logitech USB Receiver: Configuring as keyboard
[    17.850] (II) Logitech USB Receiver: Adding scrollwheel support
[    17.850] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    17.850] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.850] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input4/event4"
[    17.850] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    17.850] (**) Option "xkb_rules" "evdev"
[    17.850] (**) Option "xkb_model" "pc105"
[    17.850] (**) Option "xkb_layout" "us"
[    17.850] (II) Logitech USB Receiver: initialized for relative axes.
[    17.850] (WW) Logitech USB Receiver: ignoring absolute axes.
[    17.850] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    17.850] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    17.850] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    17.850] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    17.850] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    17.850] (II) No input driver/identifier specified (ignoring)
[    17.851] (II) config/udev: Adding input device Dexin Corp. 2.4GHz Wireless Mouse (/dev/input/event2)
[    17.851] (**) Dexin Corp. 2.4GHz Wireless Mouse: Applying InputClass "evdev pointer catchall"
[    17.851] (II) Using input driver 'evdev' for 'Dexin Corp. 2.4GHz Wireless Mouse'
[    17.851] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.851] (**) Dexin Corp. 2.4GHz Wireless Mouse: always reports core events
[    17.851] (**) Dexin Corp. 2.4GHz Wireless Mouse: Device: "/dev/input/event2"
[    17.852] (--) Dexin Corp. 2.4GHz Wireless Mouse: Found 9 mouse buttons
[    17.852] (--) Dexin Corp. 2.4GHz Wireless Mouse: Found scroll wheel(s)
[    17.852] (--) Dexin Corp. 2.4GHz Wireless Mouse: Found relative axes
[    17.852] (--) Dexin Corp. 2.4GHz Wireless Mouse: Found x and y relative axes
[    17.852] (II) Dexin Corp. 2.4GHz Wireless Mouse: Configuring as mouse
[    17.852] (II) Dexin Corp. 2.4GHz Wireless Mouse: Adding scrollwheel support
[    17.852] (**) Dexin Corp. 2.4GHz Wireless Mouse: YAxisMapping: buttons 4 and 5
[    17.852] (**) Dexin Corp. 2.4GHz Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.852] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input2/event2"
[    17.852] (II) XINPUT: Adding extended input device "Dexin Corp. 2.4GHz Wireless Mouse" (type: MOUSE)
[    17.852] (II) Dexin Corp. 2.4GHz Wireless Mouse: initialized for relative axes.
[    17.852] (**) Dexin Corp. 2.4GHz Wireless Mouse: (accel) keeping acceleration scheme 1
[    17.852] (**) Dexin Corp. 2.4GHz Wireless Mouse: (accel) acceleration profile 0
[    17.852] (**) Dexin Corp. 2.4GHz Wireless Mouse: (accel) acceleration factor: 2.000
[    17.852] (**) Dexin Corp. 2.4GHz Wireless Mouse: (accel) acceleration threshold: 4
[    17.852] (II) config/udev: Adding input device Dexin Corp. 2.4GHz Wireless Mouse (/dev/input/mouse0)
[    17.852] (II) No input driver/identifier specified (ignoring)
[    17.863] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    18.063] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    18.063] (II) fglrx(0): Using EDID range info for horizontal sync
[    18.063] (II) fglrx(0): Using EDID range info for vertical refresh
[    18.063] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.063] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    18.063] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.063] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.063] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.063] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    18.063] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.063] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.063] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.063] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.063] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.063] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.063] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.063] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.063] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.063] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.063] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.063] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    18.063] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.063] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    18.063] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    18.063] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    18.063] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.063] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    18.081] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    18.081] (II) fglrx(0): Using hsync ranges from config file
[    18.081] (II) fglrx(0): Using vrefresh ranges from config file
[    18.081] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.081] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    18.081] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.081] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.081] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.081] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    18.081] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.081] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.081] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.081] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.081] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.081] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.081] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.081] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.081] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.081] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.081] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.081] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    18.081] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.081] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    18.081] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    18.081] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    18.081] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.081] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    18.113] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    18.113] (II) fglrx(0): Using hsync ranges from config file
[    18.113] (II) fglrx(0): Using vrefresh ranges from config file
[    18.113] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.113] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    18.113] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.113] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.113] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.113] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    18.113] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.113] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.113] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.113] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.113] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.113] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.113] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.113] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.113] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.113] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.113] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.113] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    18.113] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.113] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    18.113] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    18.113] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    18.113] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.113] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    18.131] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    18.131] (II) fglrx(0): Using hsync ranges from config file
[    18.131] (II) fglrx(0): Using vrefresh ranges from config file
[    18.131] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.131] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    18.131] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.131] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.131] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.131] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    18.131] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.131] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.131] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.131] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.131] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.131] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.131] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.131] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.131] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.131] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.131] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.131] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    18.131] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.131] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    18.131] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    18.131] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    18.131] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.131] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    19.421] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse2)
[    19.421] (II) No input driver/identifier specified (ignoring)
[    19.421] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event5)
[    19.421] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    19.421] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[    19.421] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.421] (**) PS/2 Generic Mouse: always reports core events
[    19.421] (**) PS/2 Generic Mouse: Device: "/dev/input/event5"
[    19.444] (--) PS/2 Generic Mouse: Found 3 mouse buttons
[    19.444] (--) PS/2 Generic Mouse: Found relative axes
[    19.444] (--) PS/2 Generic Mouse: Found x and y relative axes
[    19.444] (II) PS/2 Generic Mouse: Configuring as mouse
[    19.444] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    19.444] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.444] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    19.444] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    19.444] (II) PS/2 Generic Mouse: initialized for relative axes.
[    19.444] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[    19.444] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[    19.444] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[    19.444] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[    33.839] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[    34.427] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    34.427] (II) fglrx(0): Using hsync ranges from config file
[    34.427] (II) fglrx(0): Using vrefresh ranges from config file
[    34.427] (II) fglrx(0): Printing DDC gathered Modelines:
[    34.427] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    34.427] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.427] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.427] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.427] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.427] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    34.427] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.427] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.427] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.427] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.427] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.427] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.427] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    34.427] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.427] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.427] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    34.427] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    34.427] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    34.427] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    34.427] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    34.427] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    34.427] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    34.427] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    34.444] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    34.445] (II) fglrx(0): Using hsync ranges from config file
[    34.445] (II) fglrx(0): Using vrefresh ranges from config file
[    34.445] (II) fglrx(0): Printing DDC gathered Modelines:
[    34.445] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    34.445] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.445] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.445] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.445] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.445] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    34.445] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.445] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.445] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.445] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.445] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.445] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.445] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    34.445] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.445] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.445] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    34.445] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    34.445] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    34.445] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    34.445] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    34.445] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    34.445] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    34.445] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    34.462] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    34.462] (II) fglrx(0): Using hsync ranges from config file
[    34.462] (II) fglrx(0): Using vrefresh ranges from config file
[    34.462] (II) fglrx(0): Printing DDC gathered Modelines:
[    34.462] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    34.462] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.462] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.462] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.462] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.462] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    34.462] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.462] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.462] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.462] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.462] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.462] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.462] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    34.462] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.462] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.462] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    34.462] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    34.462] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    34.462] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    34.462] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    34.462] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    34.462] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    34.462] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    34.479] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    34.479] (II) fglrx(0): Using hsync ranges from config file
[    34.479] (II) fglrx(0): Using vrefresh ranges from config file
[    34.479] (II) fglrx(0): Printing DDC gathered Modelines:
[    34.479] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    34.479] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    34.479] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    34.479] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    34.479] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    34.479] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    34.479] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    34.479] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    34.479] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    34.479] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.479] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    34.479] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.479] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    34.479] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    34.479] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    34.479] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    34.479] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    34.479] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    34.479] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    34.479] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    34.479] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    34.479] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    34.479] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    35.049] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    35.049] (II) fglrx(0): Using hsync ranges from config file
[    35.049] (II) fglrx(0): Using vrefresh ranges from config file
[    35.049] (II) fglrx(0): Printing DDC gathered Modelines:
[    35.049] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    35.049] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.049] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    35.049] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    35.049] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    35.049] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    35.049] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.049] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    35.049] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    35.049] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    35.049] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    35.049] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.049] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    35.049] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    35.049] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    35.049] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    35.049] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    35.049] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.049] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    35.049] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    35.049] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    35.049] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    35.049] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    40.493] (II) fglrx(0): EDID vendor "NEC", prod id 26508
[    40.493] (II) fglrx(0): Using hsync ranges from config file
[    40.493] (II) fglrx(0): Using vrefresh ranges from config file
[    40.493] (II) fglrx(0): Printing DDC gathered Modelines:
[    40.493] (II) fglrx(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[    40.493] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    40.493] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    40.493] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    40.493] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    40.493] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    40.493] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    40.493] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    40.493] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    40.493] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    40.493] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    40.493] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    40.493] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    40.493] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    40.493] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    40.493] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    40.493] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    40.493] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    40.493] (II) fglrx(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
[    40.493] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    40.493] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    40.493] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    40.493] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)[/QUOTE]The line in Red, this is what my point is about researching and not finding answers where I think there should be answers. The contents of my xorg.conf.d folder are varied, but one of them is 50-vmmouse.conf 

> Section "InputClass"
    Identifier    "vmmouse"
    MatchIsPointer    "on"
    MatchTag    "vmmouse"
    Driver        "vmmouse"
EndSection

```[QUOTE]**Package: xserver-xorg-input-vmmouse (1:12.7.0-1) **

    **Links for xserver-xorg-input-vmmouse**

     
  **Debian Resources:**

 
[LIST]
[*][Bug Reports]("http://bugs.debian.org/xserver-xorg-input-vmmouse")
[*][Developer Information (PTS)]("http://packages.qa.debian.org/xserver-xorg-input-vmmouse")
[*][Debian Changelog]("http://packages.debian.org/changelogs/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.7.0-1/changelog")
[*][Copyright File]("http://packages.debian.org/changelogs/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.7.0-1/xserver-xorg-input-vmmouse.copyright")
[*][Debian Patch Tracker]("http://patch-tracker.debian.org/package/xserver-xorg-input-vmmouse/1:12.7.0-1")
[/LIST]
     **Download Source Package [xserver-xorg-input-vmmouse]("http://packages.debian.org/source/sid/xserver-xorg-input-vmmouse"):**

        
[LIST]
[*][[xserver-xorg-input-vmmouse_12.7.0-1.dsc]]("http://ftp.de.debian.org/debian/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.7.0-1.dsc")
[*][[xserver-xorg-input-vmmouse_12.7.0.orig.tar.gz]]("http://ftp.de.debian.org/debian/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.7.0.orig.tar.gz")
[*][[xserver-xorg-input-vmmouse_12.7.0-1.diff.gz]]("http://ftp.de.debian.org/debian/pool/main/x/xserver-xorg-input-vmmouse/xserver-xorg-input-vmmouse_12.7.0-1.diff.gz")
[/LIST]
           **Maintainers:**


[LIST]
[*][EMAIL="debian-x@lists.debian.org"]Debian X Strike Force[/EMAIL]     ([QA Page]("http://qa.debian.org/developer.php?login=debian-x%40lists.debian.org"), [Mail Archive]("http://lists.debian.org/debian-x/"))
[*][EMAIL="dparsons@debian.org"]Drew Parsons[/EMAIL]     ([QA Page]("http://qa.debian.org/developer.php?login=dparsons%40debian.org"))
[*][EMAIL="kibi@debian.org"]Cyril Brulebois[/EMAIL]     ([QA Page]("http://qa.debian.org/developer.php?login=kibi%40debian.org"))
[/LIST]
             **Similar packages:**

     
[LIST]
[*][xserver-xorg-video-vmware]("http://packages.debian.org/xserver-xorg-video-vmware")
[*][xserver-xorg-input-mouse]("http://packages.debian.org/xserver-xorg-input-mouse")
[*][xserver-xorg-input-evdev]("http://packages.debian.org/xserver-xorg-input-evdev")
[*][xserver-xorg-input-penmount]("http://packages.debian.org/xserver-xorg-input-penmount")
[*][xserver-xorg-input-kbd]("http://packages.debian.org/xserver-xorg-input-kbd")
[*][xserver-xorg-input-mutouch]("http://packages.debian.org/xserver-xorg-input-mutouch")
[*][xserver-xorg-input-acecad]("http://packages.debian.org/xserver-xorg-input-acecad")
[*][xserver-xorg-input-citron]("http://packages.debian.org/xserver-xorg-input-citron")
[*][xserver-xorg-input-joystick]("http://packages.debian.org/xserver-xorg-input-joystick")
[*][xserver-xorg-input-elographics]("http://packages.debian.org/xserver-xorg-input-elographics")
[*][xserver-xorg-input-fpit]("http://packages.debian.org/xserver-xorg-input-fpit")
[/LIST]
   
       
               **X.Org X server -- VMMouse input driver to use with VMWare**

      This package provides the driver for the X11 vmmouse input device. 
 The VMMouse driver enables support for the special VMMouse protocol that is provided by VMware virtual machines to give absolute pointer positioning. 
 [COLOR=Red]The vmmouse driver is capable of falling back to the standard "mouse" driver if a VMware virtual machine is not detected.[/COLOR] This allows for dual-booting of an operating system from a virtual machine to real hardware without having to edit [xorg]("http://en.wikipedia.org/wiki/X.Org_Server").conf every time. 
Say what? 

This is my argument I'm making, about not being able to find the answers from the research. Perhaps I'm missing something, but why do I want virtualware that checks for virtualware first by default? 

I can't find answers from these instructional pages. They're not adequate, and they seem to usually just present even more questions.

I'm making valid points here, I know I am. Ignorance notwithstanding.

---

### Post by deconstrained on 2011-04-19
> **goscuter1 said:**
> The problem with investigating and Googling and looking things up...**is that 80% of the time, the instruction manuals are no help whatsoever.**

And therein lies the risk, a Wikipedia-like vortex trap, where each new question raises half a dozen more.
**NO.** Hell no. Seriously, are you trolling?

If half the people who come running to the forums "like a child running into his parents' room after a bad dream" (as eloquently stated by ED's *Ubuntu* page) had bothered reading manual pages, or *learning how to use the manual pages feature* of Unix-like systems, they WOULD figure it out for themselves.

The biggest problem with Ubuntu forums is that instead of at least using the search feature, newcomers to Linux post the same generic problems, without giving ANY detail, over and over and over again, and then other users come in and speculate as to what might be the problem, and that adds critical keywords to the post. Thus, a websearch for a specific problem will display hundreds of Ubuntu forums posts where the OP doesn't even have the problem that most of the attempting-to-be-helpful members suggested might be the problem, and the solution that the searcher needs, if it exists, is buried deeper in search terms.

But what I think is irrelevant to your post. In fact, any comment, opinion or attempt to help you would be irrelevant, because **it's painfully obvious that you're just frustrated, venting and/or trolling** because you don't have all the answers right now.

---

### Post by Kururu Souchou on 2011-04-19
> **goscuter1 said:**
> I'm just joking. 

Kind of. 

In my experience, I should have said. Then I wouldn't be joking. If anyone cares, look at my post count, see how many questions get answered here. People are helpful and cool. I know they just don't know the answers. But that's concerning. Someone should **know **the answers. 

The problem with investigating and Googling and looking things up...is that 80% of the time, the instruction manuals are no help whatsoever. 

And therein lies the risk, a Wikipedia-like vortex trap, where each new question raises half a dozen more. 

I just Googled "kworker" as I like to know things that are unexplained and doing stuff on my system. But I discovered, 100 new questions instead, and didn't get the answer for kworker (neither did these guys yet, but hopefully they'll figure it out cause they're brighter than I am): [http://ubuntuforums.org/showpost.php?p=10692493&postcount=18](http://ubuntuforums.org/showpost.php?p=10692493&postcount=18)

Then I got around into playing with ~$ last 

Look, I've read and read, and either I'm becoming senile at a very young age, or my highly-vaunted (by my Mom) embarrassingly-high IQ is a joke. But I can't learn squat or find answers to sweet jack all. 

Maybe getting some at launchpad, but as far as experts on ubuntuforums go, I haven't had much luck so gonna hang with you fine people for awhile - if that's okay of course. 

I don't expect anyone will actually have the answers for these questions, but I'm tired of Googling the whirlpool of 'experts', so it's a freeroll from where I'm sitting...

I am currently sitting alone, on a single console, and there are no other computers in my network. And no other people on my floor of this building. No one else (physically) gets within 100 yards of my single computer (the others have died ;( - fml). Strange that they did, because the experts said nothing was wrong, whilst they were dying. Of course. 

I have no desire for Virtual consoles, so why do I have recursive X11 nonsense going on? 

[http://i.imgur.com/i95Hf.png](http://i.imgur.com/i95Hf.png)

Speaking of which, why do I have X11 at all? I'm quite fond of Gnome/Nautilus, at least when it's not crashing randomly. 

Why...oh heck this question can ask itself:

```
goscuter1@j-d:~$ last -adioxF
         (to lvl 2)   Thu Jan  1 07:00:00 1970 - Tue Apr 19 06:36:22 2011 (15082+23:36 0.0.0.0
         (to lvl 2)   Thu Jan  1 07:00:00 1970 - Thu Jan  1 07:00:00 1970  (00:00)     0.0.0.0
         system boot  Thu Jan  1 07:00:00 1970 - Tue Apr 19 06:36:22 2011 (15082+23:36 0.0.0.0

```How do I manage 26 hours in a day. On one computer. 

```
goscuter1@j-d:~$ ac -dp ; uptime
    goscuter1                            3.86
Apr 17    total        3.86
    goscuter1                           26.34
    root                                 0.36
Apr 18    total       26.70
    goscuter1                            9.01
    root                                 1.44
Today    total       10.45
 06:39:40 up 41 min,  2 users,  load average: 0.05, 0.08, 0.13

```Why is there two of me logged in right now? Why do I keep jumping around from pts to pts and tty to tty? 

```
wtmp begins Sun Apr 17 21:06:31 2011
goscuter1@j-d:~$ last -ai
goscuter pts/0        Tue Apr 19 06:00   still logged in    0.0.0.0
goscuter tty7         Tue Apr 19 05:59   still logged in    0.0.0.0
reboot   system boot  Tue Apr 19 05:58 - 06:02  (00:03)     0.0.0.0
goscuter pts/2        Tue Apr 19 03:29 - down   (02:27)     0.0.0.0
goscuter pts/1        Tue Apr 19 03:29 - 03:29  (00:00)     0.0.0.0
goscuter pts/1        Tue Apr 19 03:09 - 03:09  (00:00)     0.0.0.0
goscuter pts/0        Tue Apr 19 03:08 - 03:29  (00:21)     0.0.0.0
root     pts/1        Tue Apr 19 01:19 - 02:00  (00:40)     0.0.0.0
root     pts/0        Tue Apr 19 01:15 - 02:00  (00:45)     0.0.0.0
goscuter tty7         Tue Apr 19 01:14 - down   (04:42)     0.0.0.0
reboot   system boot  Tue Apr 19 01:14 - 05:57  (04:42)     0.0.0.0
goscuter tty2         Tue Apr 19 01:11 - 01:11  (00:00)     0.0.0.0
goscuter tty2         Tue Apr 19 01:11 - 01:11  (00:00)     0.0.0.0
goscuter tty2         Tue Apr 19 00:56 - 01:11  (00:14)     0.0.0.0
goscuter tty2         Tue Apr 19 00:56 - 00:56  (00:00)     0.0.0.0
goscuter tty2         Tue Apr 19 00:55 - 00:55  (00:00)     0.0.0.0
goscuter tty2         Tue Apr 19 00:55 - 00:55  (00:00)     0.0.0.0
goscuter pts/0        Tue Apr 19 00:28 - crash  (00:46)     0.0.0.0
goscuter pts/0        Tue Apr 19 00:16 - 00:24  (00:07)     0.0.0.0
goscuter pts/1        Mon Apr 18 20:09 - 20:09  (00:00)     0.0.0.0
goscuter pts/0        Mon Apr 18 20:08 - 23:32  (03:23)     0.0.0.0
root     pts/0        Mon Apr 18 20:08 - 20:08  (00:00)     0.0.0.0
goscuter pts/1        Mon Apr 18 12:09 - 12:20  (00:11)     0.0.0.0
root     pts/1        Mon Apr 18 12:08 - 12:09  (00:00)     0.0.0.0
goscuter pts/0        Mon Apr 18 09:31 - 10:45  (01:13)     0.0.0.0
goscuter pts/0        Mon Apr 18 08:36 - 08:50  (00:13)     0.0.0.0
root     pts/0        Mon Apr 18 07:43 - 08:03  (00:20)     0.0.0.0
goscuter pts/0        Mon Apr 18 07:02 - 07:03  (00:00)     0.0.0.0
goscuter tty7         Mon Apr 18 06:54 - crash  (18:19)     0.0.0.0
reboot   system boot  Mon Apr 18 06:54 - 05:57  (23:02)     0.0.0.0
goscuter tty7         Mon Apr 18 03:21 - crash  (03:32)     0.0.0.0
reboot   system boot  Mon Apr 18 03:21 - 05:57 (1+02:36)    0.0.0.0
goscuter pts/0        Mon Apr 18 01:13 - 02:07  (00:53)     0.0.0.0
goscuter tty7         Mon Apr 18 01:07 - 03:18  (02:11)     0.0.0.0
reboot   system boot  Mon Apr 18 01:07 - 03:18  (02:11)     0.0.0.0
goscuter pts/0        Mon Apr 18 00:54 - 00:54  (00:00)     0.0.0.0
goscuter pts/0        Mon Apr 18 00:51 - 00:52  (00:00)     0.0.0.0
goscuter pts/0        Sun Apr 17 23:30 - 23:42  (00:11)     0.0.0.0
goscuter tty7         Sun Apr 17 22:21 - down   (02:44)     0.0.0.0
reboot   system boot  Sun Apr 17 22:21 - 01:06  (02:45)     0.0.0.0
goscuter tty1         Sun Apr 17 22:20 - crash  (00:01)     0.0.0.0
goscuter tty1         Sun Apr 17 22:20 - 22:20  (00:00)     0.0.0.0
goscuter tty1         Sun Apr 17 22:18 - 22:19  (00:01)     0.0.0.0
goscuter tty1         Sun Apr 17 22:18 - 22:18  (00:00)     0.0.0.0
reboot   system boot  Sun Apr 17 22:17 - 01:06  (02:48)     0.0.0.0
reboot   system boot  Sun Apr 17 22:16 - 01:06  (02:50)     0.0.0.0
goscuter pts/1        Sun Apr 17 21:49 - 21:49  (00:00)     0.0.0.0
goscuter pts/0        Sun Apr 17 21:18 - 22:14  (00:55)     0.0.0.0
goscuter tty7         Sun Apr 17 21:17 - down   (00:57)     0.0.0.0
reboot   system boot  Sun Apr 17 21:16 - 22:14  (00:57)     0.0.0.0
goscuter tty7         Sun Apr 17 21:07 - 21:15  (00:07)     0.0.0.0
reboot   system boot  Sun Apr 17 21:06 - 21:15  (00:09)     0.0.0.0

```Here are my last 2 hours worth of commands. When I say 'my', I mean...I typed 1% of them. 

So who or what is tying the rest of them? And what is with the timing being all out of order? 

I just rebooted, like right now pretty much. My only use of the terminal after booting back in was the 5 "last" commands right there with a sudo. Who's doing these other commands? I'm sick of Googling and finding non-answers.  

WAY down the list, you'll see where I learned about ~$ sudo halt

lol. 

But my next commands after that was the bolded 6 just directly below these lines. And all those commands being entered into the terminal in the minute before I pressed "halt" - that crap is not by me. I did no such commands. This is crap, basically. 

I got like 99 problems, and ubuntu is now all of them (Windows was, before). My soon-to-be-ex-girlfriend is about to tip it to 100. I need to end this ridiculous madness. But everyone says everything is fine. No problems. No answers. 

I'm tired of asking questions. And getting no answers anyway. So I'm gonna stop. If anyone wants to look out of interest, be my guest. And I'd appreciate it, of course. 

```
cat                    goscuter __         0.00 secs Tue Apr 19 06:03
which                  goscuter __         0.00 secs Tue Apr 19 06:03
compiz            F    goscuter __         0.00 secs Tue Apr 19 06:03
[B]last                   goscuter pts/0      0.00 secs Tue Apr 19 06:02
last                   goscuter pts/0      0.00 secs Tue Apr 19 06:01
last                   goscuter pts/0      0.00 secs Tue Apr 19 06:01
sudo             S     root     pts/0      0.04 secs Tue Apr 19 06:01
last             S     root     pts/0      0.00 secs Tue Apr 19 06:01
last                   goscuter pts/0      0.00 secs Tue Apr 19 06:01[/B]
compiz            F    goscuter __         0.00 secs Tue Apr 19 06:00
desktopcouch-se   F    goscuter __         0.03 secs Tue Apr 19 05:59
tty                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
apport-checkrep        goscuter __         0.06 secs Tue Apr 19 06:00
apport-checkrep        goscuter __         0.06 secs Tue Apr 19 06:00
ps                     goscuter pts/0      0.01 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
is-cache-empty         goscuter __         0.00 secs Tue Apr 19 06:00
find                   goscuter __         0.00 secs Tue Apr 19 06:00
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 06:00
apt-check              goscuter __         0.50 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
dpkg                   goscuter __         0.00 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
dpkg                   goscuter __         0.00 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
dpkg                   goscuter __         0.00 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
dpkg                   goscuter __         0.00 secs Tue Apr 19 06:00
lsb_release            goscuter __         0.02 secs Tue Apr 19 06:00
sh                     goscuter __         0.00 secs Tue Apr 19 06:00
users                  goscuter pts/0      0.00 secs Tue Apr 19 06:00
whoami                 goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
ls                     goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.03 secs Tue Apr 19 06:00
sed                    goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
uname                  goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
dircolors              goscuter pts/0      0.00 secs Tue Apr 19 06:00
bash              F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
lesspipe               goscuter pts/0      0.00 secs Tue Apr 19 06:00
lesspipe          F    goscuter pts/0      0.00 secs Tue Apr 19 06:00
dirname                goscuter pts/0      0.00 secs Tue Apr 19 06:00
basename               goscuter pts/0      0.00 secs Tue Apr 19 06:00
compiz            F    goscuter __         0.00 secs Tue Apr 19 06:00
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 06:00
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
ubuntuone-login        goscuter __         0.29 secs Tue Apr 19 05:59
ondemand               root     __         0.00 secs Tue Apr 19 05:58
sleep                  root     __         0.00 secs Tue Apr 19 05:58
ubuntu-sso-logi        goscuter __         0.21 secs Tue Apr 19 05:59
e-addressbook-f      X goscuter __         0.01 secs Tue Apr 19 05:59
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ubuntuone-launc        goscuter __         0.35 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
couchjs           F    goscuter __         0.00 secs Tue Apr 19 05:59
sed                    goscuter __         0.00 secs Tue Apr 19 05:59
couchjs           F    goscuter __         0.00 secs Tue Apr 19 05:59
getopt                 goscuter __         0.00 secs Tue Apr 19 05:59
basename               goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
ureadahead       SF    root     __         0.21 secs Tue Apr 19 05:58
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
inet_gethost           goscuter __         0.00 secs Tue Apr 19 05:59
inet_gethost      F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
indicator-datet      X goscuter __         0.03 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sleep                  root     __         0.00 secs Tue Apr 19 05:58
python                 goscuter __         0.10 secs Tue Apr 19 05:59
lockfile-remove        root     __         0.00 secs Tue Apr 19 05:59
ubuntu-geoip-pr      X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
indicator-me-se      X goscuter __         0.01 secs Tue Apr 19 05:59
indicator-sound      X goscuter __         0.00 secs Tue Apr 19 05:59
lockfile-touch         root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d            root     __         0.00 secs Tue Apr 19 05:59
ntpdate          S     root     __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
erl               F    goscuter __         0.00 secs Tue Apr 19 05:59
sed                    goscuter __         0.00 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.04 secs Tue Apr 19 05:59
erl               F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
python                 goscuter __         0.04 secs Tue Apr 19 05:59
python                 goscuter __         0.04 secs Tue Apr 19 05:59
python                 goscuter __         0.04 secs Tue Apr 19 05:59
python                 goscuter __         0.09 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.05 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
getopt                 goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
basename               goscuter __         0.00 secs Tue Apr 19 05:59
couchdb                goscuter __         0.00 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
couchdb           F    goscuter __         0.00 secs Tue Apr 19 05:59
couchdb           F    goscuter __         0.00 secs Tue Apr 19 05:59
couchdb           F    goscuter __         0.00 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
touch                  goscuter __         0.00 secs Tue Apr 19 05:59
couchdb           F    goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
getopt                 goscuter __         0.00 secs Tue Apr 19 05:59
python                 goscuter __         0.08 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
basename               goscuter __         0.00 secs Tue Apr 19 05:59
python                 goscuter __         0.03 secs Tue Apr 19 05:59
python                 goscuter __         0.02 secs Tue Apr 19 05:59
python                 goscuter __         0.02 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
net                    goscuter __         0.00 secs Tue Apr 19 05:59
gvfsd             F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
which                  goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
grep                   goscuter __         0.00 secs Tue Apr 19 05:59
lspci                  goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
grep                   goscuter __         0.00 secs Tue Apr 19 05:59
lspci                  goscuter __         0.00 secs Tue Apr 19 05:59
nm-dispatcher.a  S     root     __         0.00 secs Tue Apr 19 05:59
threaded-ml          X goscuter __         0.04 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
invoke-rc.d            root     __         0.00 secs Tue Apr 19 05:59
lockfile-create        root     __         0.00 secs Tue Apr 19 05:59
run-parts              root     __         0.00 secs Tue Apr 19 05:59
wpasupplicant          root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
wpasupplicant     F    root     __         0.00 secs Tue Apr 19 05:59
sh                     root     __         0.00 secs Tue Apr 19 05:59
sh                F    root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
status                 root     __         0.00 secs Tue Apr 19 05:59
upstart                root     __         0.00 secs Tue Apr 19 05:59
initctl                root     __         0.00 secs Tue Apr 19 05:59
openvpn                root     __         0.00 secs Tue Apr 19 05:59
ntpdate                root     __         0.00 secs Tue Apr 19 05:59
clamav-freshcla        root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch        root     __         0.00 secs Tue Apr 19 05:59
touch            S     root     __         0.00 secs Tue Apr 19 05:59
logger                 root     __         0.00 secs Tue Apr 19 05:59
killall                goscuter __         0.00 secs Tue Apr 19 05:59
invoke-rc.d            root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon           root     __         0.00 secs Tue Apr 19 05:59
stop                   root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon     SF    avahi    __         0.01 secs Tue Apr 19 05:58
avahi-daemon      F  X avahi    __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:59
status                 root     __         0.00 secs Tue Apr 19 05:59
basename               root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d       F    root     __         0.00 secs Tue Apr 19 05:59
xargs                  root     __         0.00 secs Tue Apr 19 05:59
echo                   root     __         0.00 secs Tue Apr 19 05:59
ls                     root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d       F    root     __         0.00 secs Tue Apr 19 05:59
xargs                  root     __         0.00 secs Tue Apr 19 05:59
echo                   root     __         0.00 secs Tue Apr 19 05:59
ls                     root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d       F    root     __         0.00 secs Tue Apr 19 05:59
xargs                  root     __         0.00 secs Tue Apr 19 05:59
echo                   root     __         0.00 secs Tue Apr 19 05:59
ls                     root     __         0.00 secs Tue Apr 19 05:59
invoke-rc.d       F    root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
runlevel               root     __         0.00 secs Tue Apr 19 05:59
gvfsd             F    goscuter __         0.00 secs Tue Apr 19 05:59
which                  root     __         0.00 secs Tue Apr 19 05:59
egrep                  root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
host                   root     __         0.00 secs Tue Apr 19 05:59
mv               S     root     __         0.00 secs Tue Apr 19 05:59
sort             S     root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
cat                    root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
route                  root     __         0.00 secs Tue Apr 19 05:59
zeitgeist-datah      X goscuter __         0.01 secs Tue Apr 19 05:59
which                  goscuter __         0.00 secs Tue Apr 19 05:59
start-pulseaudi        goscuter __         0.00 secs Tue Apr 19 05:59
pactl                  goscuter __         0.00 secs Tue Apr 19 05:59
pactl                  goscuter __         0.00 secs Tue Apr 19 05:59
pactl                  goscuter __         0.00 secs Tue Apr 19 05:59
pactl                  goscuter __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
egrep                  root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
avahi-daemon-ch   F    root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
ifconfig               root     __         0.00 secs Tue Apr 19 05:59
egrep                  root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
avahi-autoipd          root     __         0.00 secs Tue Apr 19 05:59
ip                     root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
ip                     root     __         0.00 secs Tue Apr 19 05:59
mv                     root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
cat                    root     __         0.00 secs Tue Apr 19 05:59
mktemp                 root     __         0.00 secs Tue Apr 19 05:59
gnome-screensav      X goscuter __         0.03 secs Tue Apr 19 05:59
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
sh                     goscuter __         0.00 secs Tue Apr 19 05:59
ldconfig.real          goscuter __         0.00 secs Tue Apr 19 05:59
nm-dhcp-client.        root     __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
nm-dhcp-client.        root     __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
syndaemon              goscuter __         0.00 secs Tue Apr 19 05:59
gvfsd             F    goscuter __         0.00 secs Tue Apr 19 05:59
gnome-settings-   F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
pulseaudio        F    goscuter __         0.00 secs Tue Apr 19 05:59
pulseaudio             goscuter __         0.00 secs Tue Apr 19 05:59
pulseaudio             goscuter __         0.00 secs Tue Apr 19 05:59
xdg-user-dirs-g        goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
docky             F    goscuter __         0.00 secs Tue Apr 19 05:59
dirname                goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:59
gnome-settings-        goscuter __         0.00 secs Tue Apr 19 05:59
gvfs-fuse-daemo        goscuter __         0.00 secs Tue Apr 19 05:59
fusermount       S     goscuter __         0.00 secs Tue Apr 19 05:59
mount            S     root     __         0.00 secs Tue Apr 19 05:59
gvfsd             F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
gnome-keyring-d        goscuter __         0.00 secs Tue Apr 19 05:59
gnome-keyring-d        goscuter __         0.00 secs Tue Apr 19 05:59
gnome-keyring-d        goscuter __         0.00 secs Tue Apr 19 05:59
gsettings-data-        goscuter __         0.00 secs Tue Apr 19 05:59
unity_support_t  S     goscuter __         0.11 secs Tue Apr 19 05:59
dbus-daemon       F  X goscuter __         0.00 secs Tue Apr 19 05:59
gconf-sanity-ch      X goscuter __         0.00 secs Tue Apr 19 05:59
dbus-launch       F    goscuter __         0.00 secs Tue Apr 19 05:59
dbus-daemon            goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
readlink               goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
xdg-user-dirs-u        goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
xhost                  goscuter __         0.00 secs Tue Apr 19 05:59
id                     goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
Xsession          F    goscuter __         0.00 secs Tue Apr 19 05:59
which                  goscuter __         0.00 secs Tue Apr 19 05:59
cat                    goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
uname                  goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
expr                   goscuter __         0.00 secs Tue Apr 19 05:59
ls                     goscuter __         0.00 secs Tue Apr 19 05:59
Xsession          F    goscuter __         0.00 secs Tue Apr 19 05:59
Xsession          F    goscuter __         0.00 secs Tue Apr 19 05:59
id                     goscuter __         0.00 secs Tue Apr 19 05:59
Default                root     __         0.00 secs Tue Apr 19 05:59
initctl                root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_probe   F    root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_test    F    root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
udev-acl.ck            root     __         0.00 secs Tue Apr 19 05:59
pam-foreground-        root     __         0.00 secs Tue Apr 19 05:59
mkdir                  root     __         0.00 secs Tue Apr 19 05:59
pam-foreground-   F    root     __         0.00 secs Tue Apr 19 05:59
cut                    root     __         0.00 secs Tue Apr 19 05:59
getent                 root     __         0.00 secs Tue Apr 19 05:59
ck-collect-sess  S     root     __         0.00 secs Tue Apr 19 05:59
ck-get-x11-serv  S     root     __         0.00 secs Tue Apr 19 05:59
gnome-settings-   F  X gdm      __         0.21 secs Tue Apr 19 05:58
gconfd-2               gdm      __         0.08 secs Tue Apr 19 05:58
dbus-daemon       F  X gdm      __         0.00 secs Tue Apr 19 05:58
gvfsd                X gdm      __         0.00 secs Tue Apr 19 05:58
udev-acl.ck            root     __         0.00 secs Tue Apr 19 05:59
pam-foreground-        root     __         0.00 secs Tue Apr 19 05:59
rm                     root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
pam-foreground-   F    root     __         0.00 secs Tue Apr 19 05:59
cut                    root     __         0.00 secs Tue Apr 19 05:59
getent                 root     __         0.00 secs Tue Apr 19 05:59
gnome-session    S   X gdm      __         0.03 secs Tue Apr 19 05:58
gconftool-2          X gdm      __         0.00 secs Tue Apr 19 05:59
metacity             X gdm      __         0.06 secs Tue Apr 19 05:58
gnome-power-man      X gdm      __         0.03 secs Tue Apr 19 05:58
gdm-simple-gree      X gdm      __         0.15 secs Tue Apr 19 05:58
gnome-keyring-d  S     goscuter __         0.00 secs Tue Apr 19 05:59
gnome-keyring-d   F    goscuter __         0.00 secs Tue Apr 19 05:59
mount.ecryptfs_  S     goscuter __         0.00 secs Tue Apr 19 05:59
cryptomgr_probe   F    root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_test    F    root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe         S     root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_test    F    root     __         0.00 secs Tue Apr 19 05:59
cryptomgr_test    F    root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:59
modprobe               root     __         0.00 secs Tue Apr 19 05:59
gdm-session-wor  SF    goscuter __         1.18 secs Tue Apr 19 05:59
xkbcomp                gdm      __         0.01 secs Tue Apr 19 05:59
pm-powersave           root     __         0.00 secs Tue Apr 19 05:58
rm                     root     __         0.00 secs Tue Apr 19 05:59
xfs_buffer             root     __         0.00 secs Tue Apr 19 05:59
wireless               root     __         0.00 secs Tue Apr 19 05:59
which                  root     __         0.00 secs Tue Apr 19 05:59
which                  root     __         0.00 secs Tue Apr 19 05:59
sched-powersave        root     __         0.00 secs Tue Apr 19 05:59
sata_alpm              root     __         0.00 secs Tue Apr 19 05:59
uname                  root     __         0.00 secs Tue Apr 19 05:59
readahead              root     __         0.00 secs Tue Apr 19 05:59
blockdev         S     root     __         0.00 secs Tue Apr 19 05:59
awk                    root     __         0.00 secs Tue Apr 19 05:59
pcie_aspm              root     __         0.00 secs Tue Apr 19 05:59
laptop-mode            root     __         0.00 secs Tue Apr 19 05:59
journal-commit         root     __         0.00 secs Tue Apr 19 05:59
mount            S     root     __         0.00 secs Tue Apr 19 05:59
xkbcomp                gdm      __         0.01 secs Tue Apr 19 05:59
xkbcomp                gdm      __         0.01 secs Tue Apr 19 05:59
dbus-send              gdm      __         0.00 secs Tue Apr 19 05:59
gdm-simple-gree   F    gdm      __         0.00 secs Tue Apr 19 05:59
lsb_release            gdm      __         0.02 secs Tue Apr 19 05:59
intel-audio-pow        root     __         0.00 secs Tue Apr 19 05:59
hal-cd-polling         root     __         0.00 secs Tue Apr 19 05:59
disable_wol            root     __         0.00 secs Tue Apr 19 05:59
anacron           F    root     __         0.00 secs Tue Apr 19 05:59
anacron                root     __         0.00 secs Tue Apr 19 05:59
start                  root     __         0.00 secs Tue Apr 19 05:59
anacron                root     __         0.00 secs Tue Apr 19 05:59
xkbcomp                gdm      __         0.00 secs Tue Apr 19 05:59
95hdparm-apm           root     __         0.00 secs Tue Apr 19 05:59
95hdparm-apm      F    root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
udevadm                root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
hdparm           S     root     __         0.00 secs Tue Apr 19 05:59
95hdparm-apm      F    root     __         0.00 secs Tue Apr 19 05:59
sed                    root     __         0.00 secs Tue Apr 19 05:59
udevadm                root     __         0.00 secs Tue Apr 19 05:59
95hdparm-apm      F    root     __         0.00 secs Tue Apr 19 05:59
grep                   root     __         0.00 secs Tue Apr 19 05:59
gnome-power-bac        gdm      __         0.00 secs Tue Apr 19 05:59
pm-powersave      F    root     __         0.00 secs Tue Apr 19 05:59
uniq                   root     __         0.00 secs Tue Apr 19 05:59
sort                   root     __         0.00 secs Tue Apr 19 05:59
pm-powersave      F    root     __         0.00 secs Tue Apr 19 05:58
rm                     root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
flock                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
upowerd           F    root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported        root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported   F    root     __         0.00 secs Tue Apr 19 05:58
tr                     root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported   F    root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported        root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported   F    root     __         0.00 secs Tue Apr 19 05:58
tr                     root     __         0.00 secs Tue Apr 19 05:58
pm-is-supported   F    root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:58
gnome-settings-        gdm      __         0.00 secs Tue Apr 19 05:58
dbus-daemon       F  X gdm      __         0.00 secs Tue Apr 19 05:58
dbus-daemon       F  X gdm      __         0.00 secs Tue Apr 19 05:58
gconf-sanity-ch      X gdm      __         0.01 secs Tue Apr 19 05:58
dbus-launch       F    gdm      __         0.00 secs Tue Apr 19 05:58
dbus-launch      S     gdm      __         0.00 secs Tue Apr 19 05:58
dbus-launch       F    gdm      __         0.00 secs Tue Apr 19 05:58
dbus-daemon            gdm      __         0.02 secs Tue Apr 19 05:58
udev-acl.ck            root     __         0.00 secs Tue Apr 19 05:58
pam-foreground-        root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
pam-foreground-   F    root     __         0.00 secs Tue Apr 19 05:58
cut                    root     __         0.00 secs Tue Apr 19 05:58
getent                 root     __         0.00 secs Tue Apr 19 05:58
ck-collect-sess        root     __         0.00 secs Tue Apr 19 05:58
Default                root     __         0.00 secs Tue Apr 19 05:58
Default           F    root     __         0.00 secs Tue Apr 19 05:58
uname                  root     __         0.00 secs Tue Apr 19 05:58
Default           F    root     __         0.00 secs Tue Apr 19 05:58
Default           F    root     __         0.00 secs Tue Apr 19 05:58
initctl                root     __         0.00 secs Tue Apr 19 05:58
setvtrgb         S     root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
ck-get-x11-disp  S     root     __         0.00 secs Tue Apr 19 05:58
rc                     root     __         0.00 secs Tue Apr 19 05:58
S99rc.local            root     __         0.00 secs Tue Apr 19 05:58
rc.local               root     __         0.00 secs Tue Apr 19 05:58
plymouthd        SF    root     __         0.36 secs Tue Apr 19 05:58
plymouth-upstar  S     root     __         0.30 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
egrep            S     root     __         0.00 secs Tue Apr 19 05:58
egrep                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
start-stop-daem   F    root     __         0.00 secs Tue Apr 19 05:58
S99ondemand            root     __         0.00 secs Tue Apr 19 05:58
start-stop-daem  S     root     __         0.00 secs Tue Apr 19 05:58
egrep            S     root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
S99grub-common         root     __         0.00 secs Tue Apr 19 05:58
grub-editenv           root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
egrep            S     root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
which                  root     __         0.00 secs Tue Apr 19 05:58
S90binfmt-suppo  S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
update-binfmts         root     __         0.00 secs Tue Apr 19 05:58
mount            S     root     __         0.00 secs Tue Apr 19 05:58
modprobe         S     root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
which                  root     __         0.00 secs Tue Apr 19 05:58
uname                  root     __         0.00 secs Tue Apr 19 05:58
S75sudo                root     __         0.00 secs Tue Apr 19 05:58
find             S     root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
0000usepeerdns         root     __         0.00 secs Tue Apr 19 05:58
readlink               root     __         0.00 secs Tue Apr 19 05:58
S70dns-clean           root     __         0.00 secs Tue Apr 19 05:58
0dns-down              root     __         0.00 secs Tue Apr 19 05:58
0dns-down         F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
ls                     root     __         0.00 secs Tue Apr 19 05:58
0dns-down         F    root     __         0.00 secs Tue Apr 19 05:58
cut                    root     __         0.00 secs Tue Apr 19 05:58
0dns-down         F    root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
S50saned               root     __         0.00 secs Tue Apr 19 05:58
S50rsync               root     __         0.00 secs Tue Apr 19 05:58
S50pulseaudio    S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
S31atieventsd          root     __         0.00 secs Tue Apr 19 05:58
S25openafs-clie        root     __         0.00 secs Tue Apr 19 05:58
fs               S     root     __         0.00 secs Tue Apr 19 05:58
afsd             S     root     __         0.04 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd             SF    root     __         0.00 secs Tue Apr 19 05:58
afsd              F    root     __         0.00 secs Tue Apr 19 05:58
pidof            S     root     __         0.00 secs Tue Apr 19 05:58
pidof            S     root     __         0.00 secs Tue Apr 19 05:58
modprobe         S     root     __         0.00 secs Tue Apr 19 05:58
S25openafs-clie   F    root     __         0.00 secs Tue Apr 19 05:58
fgrep                  root     __         0.00 secs Tue Apr 19 05:58
lsmod                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
uname                  root     __         0.00 secs Tue Apr 19 05:58
uname                  root     __         0.00 secs Tue Apr 19 05:58
S20speech-dispa        root     __         0.00 secs Tue Apr 19 05:58
S20plymouth-ups        root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20plymouth            root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20network-mana        root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20kerneloops    S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
pidof            S     root     __         0.00 secs Tue Apr 19 05:58
kerneloops       S     kernoops __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
udev-configure-   F    root     __         0.00 secs Tue Apr 19 05:58
python           S   X lp       __         0.20 secs Tue Apr 19 05:58
cups-deviced     S     root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20isc-dhcp-ser  S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
sleep                  root     __         0.00 secs Tue Apr 19 05:58
modprobe               root     tty7       0.00 secs Tue Apr 19 05:58
hp               S     lp       __         0.00 secs Tue Apr 19 05:58
usb                    root     __         0.00 secs Tue Apr 19 05:58
serial                 root     __         0.00 secs Tue Apr 19 05:58
dhcpd            S     dhcpd    __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
dhcpd            S     dhcpd    __         0.00 secs Tue Apr 19 05:58
S20hostname            root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20gdm                 root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20cron                root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh  S     root     __         0.01 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
freshclam        S     clamav   __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.01 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.01 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udevd            SF    root     __         0.00 secs Tue Apr 19 05:58
udev-configure-   F    root     __         0.00 secs Tue Apr 19 05:58
sh                     root     __         0.00 secs Tue Apr 19 05:58
udev-configure-        root     __         0.00 secs Tue Apr 19 05:58
udev-configure-        root     __         0.00 secs Tue Apr 19 05:58
sh                F    root     __         0.00 secs Tue Apr 19 05:58
udevadm                root     __         0.00 secs Tue Apr 19 05:58
udevadm                root     __         0.00 secs Tue Apr 19 05:58
sleep                  root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
expr                   root     __         0.00 secs Tue Apr 19 05:58
tput             S     root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
tput                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
pidof            S     root     __         0.00 secs Tue Apr 19 05:58
dbus-daemon       F  X messageb __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
plymouth               root     __         0.00 secs Tue Apr 19 05:58
dirname                root     __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
mkdir                  root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
head                   root     __         0.00 secs Tue Apr 19 05:58
sh                     root     __         0.00 secs Tue Apr 19 05:58
chgrp                  root     __         0.00 secs Tue Apr 19 05:58
dmesg                  root     __         0.00 secs Tue Apr 19 05:58
sleep                  root     __         0.00 secs Tue Apr 19 05:58
grep                   root     __         0.00 secs Tue Apr 19 05:58
S20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:58
awk                    root     __         0.00 secs Tue Apr 19 05:58
egrep                  root     __         0.00 secs Tue Apr 19 05:58
savelog                root     __         0.00 secs Tue Apr 19 05:58
mv                     root     __         0.00 secs Tue Apr 19 05:58
ln                     root     __         0.00 secs Tue Apr 19 05:58
S20bootlogd            root     __         0.00 secs Tue Apr 19 05:58
egrep            S     root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
S20avahi-daemon        root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
S20anacron             root     __         0.00 secs Tue Apr 19 05:58
start                  root     __         0.00 secs Tue Apr 19 05:58
grep             S     root     __         0.00 secs Tue Apr 19 05:58
status                 root     __         0.00 secs Tue Apr 19 05:58
basename               root     __         0.00 secs Tue Apr 19 05:58
chmod            S     root     __         0.00 secs Tue Apr 19 05:58
chown            S     root     __         0.00 secs Tue Apr 19 05:58
touch                  root     __         0.00 secs Tue Apr 19 05:58
S20acct                root     __         0.00 secs Tue Apr 19 05:58
accton           S     root     __         0.00 secs Tue Apr 19 05:58
plymouthd              root     __         0.00 secs Tue Apr 19 05:57
gdm-binary       S   X root     __         0.02 secs Tue Apr 19 01:14
gdm-simple-slav  S   X root     __         0.01 secs Tue Apr 19 01:14
Xorg             S     root     tty7     664.72 secs Tue Apr 19 01:14
S20sendsigs       F    root     __         0.00 secs Tue Apr 19 05:57
sed                    root     __         0.00 secs Tue Apr 19 05:57
initctl                root     __         0.00 secs Tue Apr 19 05:57
S10unattended-u        root     __         0.00 secs Tue Apr 19 05:57
python           S     root     __         0.02 secs Tue Apr 19 05:57
firegl            F    root     __         0.00 secs Tue Apr 19 01:14
firegl            F    root     __         0.00 secs Tue Apr 19 01:14
firegl            F    root     __         0.00 secs Tue Apr 19 01:14
K80openvpn       S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
ls                     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
K31atieventsd          root     __         0.00 secs Tue Apr 19 05:57
K20speech-dispa        root     __         0.00 secs Tue Apr 19 05:57
K20plymouth-ups        root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20plymouth            root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20openafs-clie        root     __         0.00 secs Tue Apr 19 05:57
K20openafs-clie   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
lsmod                  root     __         0.00 secs Tue Apr 19 05:57
start-stop-daem  S     root     __         0.00 secs Tue Apr 19 05:57
pidof            S     root     __         0.00 secs Tue Apr 19 05:57
pidof            S     root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
uname                  root     __         0.00 secs Tue Apr 19 05:57
K20network-mana        root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20isc-dhcp-ser  S     root     __         0.00 secs Tue Apr 19 05:57
rm               S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
start-stop-daem        root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
K20hostname            root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20gdm                 root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20cron                root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh  S     root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
sleep                  root     __         0.00 secs Tue Apr 19 05:57
compiz           S   X goscuter __       226.35 secs Tue Apr 19 01:14
desktopcouch-se   F    goscuter __         8.23 secs Tue Apr 19 01:15
kerneloops        F    kernoops __         0.33 secs Tue Apr 19 01:14
dbus-daemon      SF  X root     __         0.00 secs Tue Apr 19 01:15
sh                     goscuter __         0.00 secs Tue Apr 19 01:15
unity-window-de      X goscuter __        12.59 secs Tue Apr 19 01:15
gdu-notificatio        goscuter __         0.02 secs Tue Apr 19 01:15
bash                   goscuter pts/2      0.22 secs Tue Apr 19 03:29
gnome-pty-helpe        goscuter __         0.00 secs Tue Apr 19 03:08
shutter              X goscuter __         3.90 secs Tue Apr 19 01:14
docky                X goscuter __        72.17 secs Tue Apr 19 01:14
gnome-screensav   F    goscuter __         0.03 secs Tue Apr 19 01:15
notify-osd           X goscuter __         4.46 secs Tue Apr 19 01:14
ssh-agent         F    goscuter __         0.00 secs Tue Apr 19 01:14
gvfs-fuse-daemo   F    goscuter __         0.01 secs Tue Apr 19 01:14
fusermount       S     goscuter __         0.00 secs Tue Apr 19 05:57
umount           S     root     __         0.00 secs Tue Apr 19 05:57
soffice.bin          X goscuter __        34.07 secs Tue Apr 19 04:36
nm-applet            X goscuter __         0.73 secs Tue Apr 19 01:14
gconfd-2               goscuter __         2.48 secs Tue Apr 19 01:14
modem-manager    S     root     __         0.01 secs Tue Apr 19 01:14
polkitd          S   X root     __         1.20 secs Tue Apr 19 01:14
console-kit-dae  S   X root     __         0.23 secs Tue Apr 19 01:14
udisks-daemon    S   X root     __         0.29 secs Tue Apr 19 01:14
system-service-  S   X root     __         0.07 secs Tue Apr 19 01:16
dbus-daemon      SF  X messageb __         1.04 secs Tue Apr 19 01:14
wpa_supplicant   S     root     __         0.00 secs Tue Apr 19 01:14
upowerd          S   X root     __         0.03 secs Tue Apr 19 01:14
udisks-daemon     F  X root     __         1.00 secs Tue Apr 19 01:14
rtkit-daemon     S   X rtkit    __         0.04 secs Tue Apr 19 01:14
hwclock          S     root     __         0.26 secs Tue Apr 19 05:57
flush-0:21        F    root     __         0.00 secs Tue Apr 19 05:57
firefox-bin          X goscuter __       1537.68 secs Tue Apr 19 01:18
plugin-containe      X goscuter __       162.63 secs Tue Apr 19 01:19
unity-panel-ser      X goscuter __       119.13 secs Tue Apr 19 01:15
gedit                X goscuter __        27.97 secs Tue Apr 19 03:47
indicator-appli      X goscuter __         0.42 secs Tue Apr 19 01:15
geoclue-master       X goscuter __         0.03 secs Tue Apr 19 01:15
unity-files-dae      X goscuter __         0.74 secs Tue Apr 19 01:15
indicator-sessi      X goscuter __         0.03 secs Tue Apr 19 01:15
indicator-datet      X goscuter __         0.03 secs Tue Apr 19 01:15
indicator-messa      X goscuter __         0.03 secs Tue Apr 19 01:15
indicator-me-se      X goscuter __         0.04 secs Tue Apr 19 01:15
nautilus             X goscuter __       269.51 secs Tue Apr 19 01:14
gvfsd-metadata         goscuter __         0.02 secs Tue Apr 19 01:15
dconf-service        X goscuter __         0.07 secs Tue Apr 19 01:15
vino-server          X goscuter __         1.48 secs Tue Apr 19 01:14
update-notifier      X goscuter __         0.31 secs Tue Apr 19 01:15
indicator-sound      X goscuter __         0.13 secs Tue Apr 19 01:15
ubuntuone-syncd      X goscuter __        13.70 secs Tue Apr 19 01:15
unity-applicati      X goscuter __         0.50 secs Tue Apr 19 01:15
gnome-terminal       X goscuter __        21.71 secs Tue Apr 19 03:08
desktopcouch-se        goscuter __         8.94 secs Tue Apr 19 01:15
gvfsd-computer         goscuter __         0.01 secs Tue Apr 19 01:15
indicator-weath      X goscuter __         1.80 secs Tue Apr 19 01:14
mission-control        goscuter __         0.03 secs Tue Apr 19 01:15
gvfs-afc-volume      X goscuter __         0.00 secs Tue Apr 19 01:14
polkit-gnome-au      X goscuter __         0.20 secs Tue Apr 19 01:14
cat                    goscuter __         0.00 secs Tue Apr 19 01:15
applet.py              goscuter __         4.01 secs Tue Apr 19 01:15
zeitgeist-daemo      X goscuter __         6.06 secs Tue Apr 19 01:14
zeitgeist-datah      X goscuter __         0.12 secs Tue Apr 19 01:14
gvfsd-burn             goscuter __         0.00 secs Tue Apr 19 01:15
gvfs-gphoto2-vo        goscuter __         0.00 secs Tue Apr 19 01:15
gvfsd-trash            goscuter __         0.03 secs Tue Apr 19 01:15
gvfs-gdu-volume        goscuter __         0.04 secs Tue Apr 19 01:14
gvfsd                  goscuter __         0.92 secs Tue Apr 19 01:14
freshclam         F    clamav   __         6.34 secs Tue Apr 19 01:14
tput             S     root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
plymouth               root     __         0.00 secs Tue Apr 19 05:57
expr                   root     __         0.00 secs Tue Apr 19 05:57
tput             S     root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
tput                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh  SF    root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh  SF    root     __         0.00 secs Tue Apr 19 05:57
dirname                root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
alsa-source       F  X goscuter __         0.11 secs Tue Apr 19 01:14
awk                    root     __         0.00 secs Tue Apr 19 05:57
head                   root     __         0.00 secs Tue Apr 19 05:57
grep                   root     __         0.00 secs Tue Apr 19 05:57
K20clamav-fresh   F    root     __         0.00 secs Tue Apr 19 05:57
awk                    root     __         0.00 secs Tue Apr 19 05:57
egrep                  root     __         0.00 secs Tue Apr 19 05:57
gconf-helper         X goscuter __         0.00 secs Tue Apr 19 01:14
gnome-settings-   F  X goscuter __         6.28 secs Tue Apr 19 01:14
gnome-session    S   X goscuter __         0.11 secs Tue Apr 19 01:14
dbus-daemon       F  X goscuter __        14.62 secs Tue Apr 19 01:14
bamfdaemon             goscuter __         2.45 secs Tue Apr 19 01:15
K20bootlogd            root     __         0.00 secs Tue Apr 19 05:57
egrep            S     root     __         0.00 secs Tue Apr 19 05:57
Default                root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
K20avahi-daemon        root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
basename               root     __         0.00 secs Tue Apr 19 05:57
K20anacron             root     __         0.00 secs Tue Apr 19 05:57
grep             S     root     __         0.00 secs Tue Apr 19 05:57
status                 root     __         0.00 secs Tue Apr 19 05:57
upstart-udev-br   F    root     __         0.07 secs Tue Apr 19 01:14
alsactl          S     root     __         0.01 secs Tue Apr 19 05:57
udev-acl.ck            root     __         0.00 secs Tue Apr 19 05:57
sh                     root     __         0.00 secs Tue Apr 19 05:57
sh                     root     __         0.00 secs Tue Apr 19 05:57
dd                     root     __         0.00 secs Tue Apr 19 05:57
stat                   root     __         0.00 secs Tue Apr 19 05:57
sh                F    root     __         0.00 secs Tue Apr 19 05:57
sed                    root     __         0.00 secs Tue Apr 19 05:57
pam-foreground-        root     __         0.00 secs Tue Apr 19 05:57
rm                     root     __         0.00 secs Tue Apr 19 05:57
sh                F    root     __         0.00 secs Tue Apr 19 05:57
sed                    root     __         0.00 secs Tue Apr 19 05:57
NetworkManager   SF  X root     __         0.34 secs Tue Apr 19 01:14
pam-foreground-   F    root     __         0.00 secs Tue Apr 19 05:57
cut                    root     __         0.00 secs Tue Apr 19 05:57
getent                 root     __         0.00 secs Tue Apr 19 05:57
getty                X root     tty6       0.00 secs Tue Apr 19 01:14
plymouth-upstar  S     root     __         0.00 secs Tue Apr 19 05:57
getty                X root     tty1       0.00 secs Tue Apr 19 01:14
gnome-keyring-d   F  X goscuter __         0.10 secs Tue Apr 19 01:14
getty                X root     tty3       0.00 secs Tue Apr 19 01:14
getty                X root     tty2       0.00 secs Tue Apr 19 01:14
cupsd            S     root     __         0.03 secs Tue Apr 19 01:14
upstart-socket-   F    root     __         0.02 secs Tue Apr 19 01:14
gdm-session-wor  S   X root     __         0.06 secs Tue Apr 19 01:14
acpid            SF    root     __         0.00 secs Tue Apr 19 01:14
cron              F  X root     __         0.01 secs Tue Apr 19 01:14
basename               root     __         0.00 secs Tue Apr 19 05:57
atd               F    root     __         0.00 secs Tue Apr 19 01:14
getty                X root     tty5       0.00 secs Tue Apr 19 01:14
irqbalance       SF  X root     __         6.78 secs Tue Apr 19 01:14
stty             S     root     __         0.00 secs Tue Apr 19 05:57
rsyslogd         SF    syslog   __         0.06 secs Tue Apr 19 01:14
udevd            SF    root     __         0.00 secs Tue Apr 19 01:14
udevd            SF    root     __         0.05 secs Tue Apr 19 01:14
udevd            SF    root     __         0.00 secs Tue Apr 19 01:14
getty                X root     tty4       0.00 secs Tue Apr 19 01:14
shutdown         SF    root     pts/2      0.00 secs Tue Apr 19 05:57
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:57
shutdown         S     root     pts/2      0.00 secs Tue Apr 19 05:57
[COLOR=Black]**halt                   goscuter pts/2      0.00 secs Tue Apr 19 05:57**[/COLOR]
[B][COLOR=Red]info                 X goscuter pts/2      0.00 secs Tue Apr 19 05:56
man                    goscuter pts/2      0.01 secs Tue Apr 19 05:56
pager                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
col                    goscuter pts/2      0.00 secs Tue Apr 19 05:56
nroff                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
groff                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
grotty                 goscuter pts/2      0.01 secs Tue Apr 19 05:56
troff                  goscuter pts/2      0.02 secs Tue Apr 19 05:56
tbl                    goscuter pts/2      0.00 secs Tue Apr 19 05:56
preconv                goscuter pts/2      0.00 secs Tue Apr 19 05:56
locale                 goscuter pts/2      0.00 secs Tue Apr 19 05:56[/COLOR][/B]
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
man               F    goscuter pts/2      0.00 secs Tue Apr 19 05:56
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:56
kworker/2:3       F    root     __         0.00 secs Tue Apr 19 05:51
kworker/2:2       F    root     __         0.00 secs Tue Apr 19 05:51
kworker/6:0       F    root     __         0.00 secs Tue Apr 19 04:09
whoami                 goscuter pts/2      0.00 secs Tue Apr 19 05:55
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:55
users            S     root     pts/2      0.00 secs Tue Apr 19 05:55
users                  goscuter pts/2      0.00 secs Tue Apr 19 05:55
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:45
ls                     goscuter pts/2      0.00 secs Tue Apr 19 05:55
ls                     goscuter pts/2      0.00 secs Tue Apr 19 05:55
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 05:55
python                 goscuter pts/2      0.13 secs Tue Apr 19 05:55
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 05:55
python                 goscuter pts/2      0.14 secs Tue Apr 19 05:55
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:55
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:54
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:54
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:54
kworker/1:3       F    root     __         0.00 secs Tue Apr 19 05:46
kworker/5:3       F    root     __         0.00 secs Tue Apr 19 05:48
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:53
killall                goscuter pts/2      0.00 secs Tue Apr 19 05:53
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:53
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:53
pidof                  goscuter pts/2      0.00 secs Tue Apr 19 05:53
kworker/0:0       F    root     __         0.01 secs Tue Apr 19 05:43
kworker/5:2       F    root     __         0.00 secs Tue Apr 19 05:22
kworker/1:0       F    root     __         0.00 secs Tue Apr 19 05:46
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:50
last             S     root     pts/2      0.00 secs Tue Apr 19 05:50
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:50
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 05:40
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:50
lastb                  goscuter pts/2      0.00 secs Tue Apr 19 05:48
kworker/0:2       F    root     __         0.00 secs Tue Apr 19 05:38
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:47
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:47
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:34
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:45
last             S     root     pts/2      0.00 secs Tue Apr 19 05:45
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:44
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:43
last             S     root     pts/2      0.00 secs Tue Apr 19 05:43
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:43
last             S     root     pts/2      0.00 secs Tue Apr 19 05:43
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 05:33
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:43
last             S     root     pts/2      0.01 secs Tue Apr 19 05:43
sudo             S     root     pts/2      0.04 secs Tue Apr 19 05:42
last             S     root     pts/2      0.00 secs Tue Apr 19 05:42
last                   goscuter pts/2      0.00 secs Tue Apr 19 05:41
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:17
powertop         S     root     pts/2      1.48 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
sh                     root     pts/2      0.00 secs Tue Apr 19 05:41
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:41
modprobe               root     __         0.00 secs Tue Apr 19 05:41
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
sh                     root     pts/2      0.00 secs Tue Apr 19 05:40
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
sh                     root     pts/2      0.00 secs Tue Apr 19 05:40
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
sh                     root     pts/2      0.00 secs Tue Apr 19 05:40
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
sh                     root     pts/2      0.00 secs Tue Apr 19 05:40
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:40
modprobe               root     __         0.00 secs Tue Apr 19 05:40
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
sh                     root     pts/2      0.00 secs Tue Apr 19 05:39
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
sh                     root     pts/2      0.00 secs Tue Apr 19 05:39
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
sh                     root     pts/2      0.00 secs Tue Apr 19 05:39
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:39
modprobe               root     __         0.00 secs Tue Apr 19 05:39
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
sh                     root     pts/2      0.00 secs Tue Apr 19 05:38
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
sh                     root     pts/2      0.00 secs Tue Apr 19 05:38
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
sh                     root     pts/2      0.00 secs Tue Apr 19 05:38
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
sh                     root     pts/2      0.00 secs Tue Apr 19 05:38
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:38
modprobe               root     __         0.00 secs Tue Apr 19 05:38
kworker/0:2       F    root     __         0.01 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
sh                     root     pts/2      0.00 secs Tue Apr 19 05:37
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:37
modprobe               root     __         0.00 secs Tue Apr 19 05:37
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
sh                     root     pts/2      0.00 secs Tue Apr 19 05:36
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
sh                     root     pts/2      0.00 secs Tue Apr 19 05:36
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
sh                     root     pts/2      0.00 secs Tue Apr 19 05:36
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:36
modprobe               root     __         0.00 secs Tue Apr 19 05:36
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
sh                     root     pts/2      0.00 secs Tue Apr 19 05:35
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
sh                     root     pts/2      0.00 secs Tue Apr 19 05:35
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
sh                     root     pts/2      0.00 secs Tue Apr 19 05:35
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
sh                     root     pts/2      0.00 secs Tue Apr 19 05:35
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:35
modprobe               root     __         0.00 secs Tue Apr 19 05:35
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
sh                     root     pts/2      0.00 secs Tue Apr 19 05:34
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
sh                     root     pts/2      0.00 secs Tue Apr 19 05:34
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
sh                     root     pts/2      0.00 secs Tue Apr 19 05:34
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
sh                     root     pts/2      0.00 secs Tue Apr 19 05:34
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:34
modprobe               root     __         0.00 secs Tue Apr 19 05:34
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
sh                     root     pts/2      0.00 secs Tue Apr 19 05:33
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
sh                     root     pts/2      0.00 secs Tue Apr 19 05:33
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
sh                     root     pts/2      0.00 secs Tue Apr 19 05:33
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:33
modprobe               root     __         0.00 secs Tue Apr 19 05:33
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
sh                     root     pts/2      0.00 secs Tue Apr 19 05:32
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
sh                     root     pts/2      0.00 secs Tue Apr 19 05:32
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
sh                     root     pts/2      0.00 secs Tue Apr 19 05:32
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
sh                     root     pts/2      0.00 secs Tue Apr 19 05:32
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:32
modprobe               root     __         0.00 secs Tue Apr 19 05:32
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
sh                     root     pts/2      0.00 secs Tue Apr 19 05:31
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
sh                     root     pts/2      0.00 secs Tue Apr 19 05:31
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
sh                     root     pts/2      0.00 secs Tue Apr 19 05:31
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:31
modprobe               root     __         0.00 secs Tue Apr 19 05:31
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
sh                     root     pts/2      0.00 secs Tue Apr 19 05:30
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
sh                     root     pts/2      0.00 secs Tue Apr 19 05:30
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
sh                     root     pts/2      0.00 secs Tue Apr 19 05:30
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:30
modprobe               root     __         0.00 secs Tue Apr 19 05:30
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
sh                     root     pts/2      0.00 secs Tue Apr 19 05:29
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
sh                     root     pts/2      0.00 secs Tue Apr 19 05:29
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
sh                     root     pts/2      0.00 secs Tue Apr 19 05:29
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
sh                     root     pts/2      0.00 secs Tue Apr 19 05:29
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:29
modprobe               root     __         0.00 secs Tue Apr 19 05:29
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
sh                     root     pts/2      0.00 secs Tue Apr 19 05:28
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
sh                     root     pts/2      0.00 secs Tue Apr 19 05:28
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
sh                     root     pts/2      0.00 secs Tue Apr 19 05:28
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:28
modprobe               root     __         0.00 secs Tue Apr 19 05:28
kworker/0:2       F    root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
sh                     root     pts/2      0.00 secs Tue Apr 19 05:27
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/1:3       F    root     __         0.00 secs Tue Apr 19 05:22
kworker/1:0       F    root     __         0.00 secs Tue Apr 19 05:22
kworker/5:0       F    root     __         0.00 secs Tue Apr 19 02:06
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
sh                     root     pts/2      0.00 secs Tue Apr 19 05:27
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
sh                     root     pts/2      0.00 secs Tue Apr 19 05:27
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:27
modprobe               root     __         0.00 secs Tue Apr 19 05:27
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
sh                     root     pts/2      0.00 secs Tue Apr 19 05:26
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
sh                     root     pts/2      0.00 secs Tue Apr 19 05:26
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
sh                     root     pts/2      0.00 secs Tue Apr 19 05:26
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:26
modprobe               root     __         0.00 secs Tue Apr 19 05:26
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
sh                     root     pts/2      0.00 secs Tue Apr 19 05:25
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
sh                     root     pts/2      0.00 secs Tue Apr 19 05:25
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
sh                     root     pts/2      0.00 secs Tue Apr 19 05:25
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
sh                     root     pts/2      0.00 secs Tue Apr 19 05:25
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:25
modprobe               root     __         0.00 secs Tue Apr 19 05:25
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
sh                     root     pts/2      0.00 secs Tue Apr 19 05:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
sh                     root     pts/2      0.00 secs Tue Apr 19 05:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
sh                     root     pts/2      0.00 secs Tue Apr 19 05:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:24
modprobe               root     __         0.00 secs Tue Apr 19 05:24
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:13
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
sh                     root     pts/2      0.00 secs Tue Apr 19 05:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
sh                     root     pts/2      0.00 secs Tue Apr 19 05:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
sh                     root     pts/2      0.00 secs Tue Apr 19 05:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
sh                     root     pts/2      0.00 secs Tue Apr 19 05:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:23
modprobe               root     __         0.00 secs Tue Apr 19 05:23
kworker/0:0       F    root     __         0.01 secs Tue Apr 19 05:12
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
sh                     root     pts/2      0.00 secs Tue Apr 19 05:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
sh                     root     pts/2      0.00 secs Tue Apr 19 05:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
sh                     root     pts/2      0.00 secs Tue Apr 19 05:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
sh                     root     pts/2      0.00 secs Tue Apr 19 05:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:22
modprobe               root     __         0.00 secs Tue Apr 19 05:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
sh                     root     pts/2      0.00 secs Tue Apr 19 05:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
sh                     root     pts/2      0.00 secs Tue Apr 19 05:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
sh                     root     pts/2      0.00 secs Tue Apr 19 05:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:21
modprobe               root     __         0.00 secs Tue Apr 19 05:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
sh                     root     pts/2      0.00 secs Tue Apr 19 05:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
sh                     root     pts/2      0.00 secs Tue Apr 19 05:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
sh                     root     pts/2      0.00 secs Tue Apr 19 05:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
sh                     root     pts/2      0.00 secs Tue Apr 19 05:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:20
modprobe               root     __         0.00 secs Tue Apr 19 05:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
sh                     root     pts/2      0.00 secs Tue Apr 19 05:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
sh                     root     pts/2      0.00 secs Tue Apr 19 05:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
sh                     root     pts/2      0.00 secs Tue Apr 19 05:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:19
modprobe               root     __         0.00 secs Tue Apr 19 05:19
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 05:08
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
sh                     root     pts/2      0.00 secs Tue Apr 19 05:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
sh                     root     pts/2      0.00 secs Tue Apr 19 05:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
sh                     root     pts/2      0.00 secs Tue Apr 19 05:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
sh                     root     pts/2      0.00 secs Tue Apr 19 05:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:18
modprobe               root     __         0.00 secs Tue Apr 19 05:18
kworker/0:2       F    root     __         0.01 secs Tue Apr 19 05:07
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
xrandr           S     root     pts/2      0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 05:17
modprobe               root     __         0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
iwpriv                 root     pts/2      0.00 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.06 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.05 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.03 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
lspci                  root     pts/2      0.06 secs Tue Apr 19 05:17
sh                     root     pts/2      0.00 secs Tue Apr 19 05:17
modprobe               root     pts/2      0.00 secs Tue Apr 19 05:17
cron             SF    root     __         0.00 secs Tue Apr 19 05:17
sh               S     root     __         0.00 secs Tue Apr 19 05:17
run-parts              root     __         0.00 secs Tue Apr 19 05:17
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 05:14
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 05:03
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 05:02
grep                   goscuter pts/2      0.00 secs Tue Apr 19 05:12
grep                   goscuter pts/2      0.00 secs Tue Apr 19 05:11
uname                  goscuter pts/2      0.00 secs Tue Apr 19 05:11
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:57
grep                   goscuter pts/2      0.00 secs Tue Apr 19 05:08
ps                     goscuter pts/2      0.00 secs Tue Apr 19 05:08
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:07
grep             S   X root     pts/2      0.01 secs Tue Apr 19 05:07
kworker/0:2       F    root     __         0.00 secs Tue Apr 19 04:57
sudo             S     root     pts/2      0.00 secs Tue Apr 19 05:04
lastcomm         S     root     pts/2      0.00 secs Tue Apr 19 05:04
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:52
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:52
sudo             S     root     pts/2      0.10 secs Tue Apr 19 05:01
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 05:01
iwpriv                 goscuter pts/2      0.00 secs Tue Apr 19 05:00
domainname             goscuter __         0.00 secs Tue Apr 19 04:59
kworker/0:2       F    root     __         0.01 secs Tue Apr 19 04:47
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:47
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:42
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:41
kworker/3:3       F    root     __         0.00 secs Tue Apr 19 03:49
kworker/7:3       F    root     __         0.00 secs Tue Apr 19 04:46
kworker/7:0       F    root     __         0.00 secs Tue Apr 19 04:46
kworker/6:3       F    root     __         0.00 secs Tue Apr 19 04:42
kworker/6:1       F    root     __         0.00 secs Tue Apr 19 04:42
kworker/0:2       F    root     __         0.00 secs Tue Apr 19 04:37
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:35
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 04:44
kworker/0:0       F    root     __         0.01 secs Tue Apr 19 04:32
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:30
kworker/0:2       F    root     __         0.68 secs Tue Apr 19 01:40
sh                     goscuter __         0.00 secs Tue Apr 19 04:36
sh                     goscuter __         0.00 secs Tue Apr 19 04:36
paperconf              goscuter __         0.00 secs Tue Apr 19 04:36
libreoffice            goscuter __         0.00 secs Tue Apr 19 04:36
soffice                goscuter __         0.00 secs Tue Apr 19 04:36
oosplash.bin         X goscuter __         0.01 secs Tue Apr 19 04:36
uname                  goscuter __         0.00 secs Tue Apr 19 04:36
javaldx                goscuter __         0.01 secs Tue Apr 19 04:36
pagein                 goscuter __         0.04 secs Tue Apr 19 04:36
oosplash.bin           goscuter __         0.00 secs Tue Apr 19 04:36
uname                  goscuter __         0.00 secs Tue Apr 19 04:36
basename               goscuter __         0.00 secs Tue Apr 19 04:36
soffice           F    goscuter __         0.00 secs Tue Apr 19 04:36
dirname                goscuter __         0.00 secs Tue Apr 19 04:36
soffice           F    goscuter __         0.00 secs Tue Apr 19 04:36
stat                   goscuter __         0.00 secs Tue Apr 19 04:36
compiz            F    goscuter __         0.00 secs Tue Apr 19 04:36
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:25
gedit                  goscuter __         0.03 secs Tue Apr 19 04:33
nautilus          F    goscuter __         0.00 secs Tue Apr 19 04:33
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:33
lastcomm         S     root     pts/2      0.01 secs Tue Apr 19 04:33
kworker/7:3       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/3:1       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/7:0       F    root     __         0.00 secs Tue Apr 19 03:14
kworker/3:0       F    root     __         0.00 secs Tue Apr 19 04:27
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:22
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:32
lastcomm         S     root     pts/2      0.01 secs Tue Apr 19 04:32
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:19
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:27
lastcomm         S     root     pts/2      0.01 secs Tue Apr 19 04:27
kworker/0:3       F    root     __         0.01 secs Tue Apr 19 04:17
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:25
ps                     goscuter pts/2      0.01 secs Tue Apr 19 04:25
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:25
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:25
ps               S     root     pts/2      0.03 secs Tue Apr 19 04:25
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:17
powertop         S     root     pts/2      0.50 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:14
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
sh                     root     pts/2      0.00 secs Tue Apr 19 04:24
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:24
modprobe               root     __         0.00 secs Tue Apr 19 04:24
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
sh                     root     pts/2      0.00 secs Tue Apr 19 04:23
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:23
modprobe               root     __         0.00 secs Tue Apr 19 04:23
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:12
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
sh                     root     pts/2      0.00 secs Tue Apr 19 04:22
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:22
modprobe               root     __         0.00 secs Tue Apr 19 04:22
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
sh                     root     pts/2      0.00 secs Tue Apr 19 04:21
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:21
modprobe               root     __         0.00 secs Tue Apr 19 04:21
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
sh                     root     pts/2      0.00 secs Tue Apr 19 04:20
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:20
modprobe               root     __         0.00 secs Tue Apr 19 04:20
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
sh                     root     pts/2      0.00 secs Tue Apr 19 04:19
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:19
modprobe               root     __         0.00 secs Tue Apr 19 04:19
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:18
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:18
modprobe               root     __         0.00 secs Tue Apr 19 04:18
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
xrandr           S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
iwpriv           S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
kworker/u:4       F    root     __         0.00 secs Tue Apr 19 04:17
modprobe               root     __         0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
iwpriv                 root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.03 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.04 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
lspci                  root     pts/2      0.06 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
modprobe               root     pts/2      0.00 secs Tue Apr 19 04:17
apt-check              goscuter __         0.45 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
sh                     goscuter __         0.00 secs Tue Apr 19 04:17
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:17
lsb_release            goscuter __         0.02 secs Tue Apr 19 04:17
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:17
apt-get          S     root     pts/2      0.34 secs Tue Apr 19 04:17
apt-get           F    root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
touch                  root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/0      0.07 secs Tue Apr 19 04:17
dpkg             S     root     pts/0      0.25 secs Tue Apr 19 04:17
frontend               root     pts/0      0.16 secs Tue Apr 19 04:17
man-db.postinst        root     pts/0      0.00 secs Tue Apr 19 04:17
mandb            S     man      pts/0      0.04 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
mandb             F    man      pts/0      0.00 secs Tue Apr 19 04:17
man-db.config          root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/0      0.00 secs Tue Apr 19 04:17
stty                   root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/0      0.00 secs Tue Apr 19 04:17
stty                   root     pts/0      0.00 secs Tue Apr 19 04:17
locale                 root     pts/0      0.00 secs Tue Apr 19 04:17
rm                     root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb               root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb               root     pts/0      0.00 secs Tue Apr 19 04:17
tar                    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-deb          F    root     pts/0      0.00 secs Tue Apr 19 04:17
dpkg-split             root     pts/0      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg-preconfigu  S     root     pts/2      0.13 secs Tue Apr 19 04:17
dpkg-preconfigu   F    root     pts/2      0.00 secs Tue Apr 19 04:17
apt-extracttemp        root     pts/2      0.01 secs Tue Apr 19 04:17
gzip                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
stty                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh               S     root     pts/2      0.00 secs Tue Apr 19 04:17
stty                   root     pts/2      0.00 secs Tue Apr 19 04:17
locale                 root     pts/2      0.00 secs Tue Apr 19 04:17
http                   root     pts/2      0.00 secs Tue Apr 19 04:17
http                   root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
sh                     root     pts/2      0.00 secs Tue Apr 19 04:17
dpkg             S     root     pts/2      0.00 secs Tue Apr 19 04:17
kworker/0:3       F    root     __         0.00 secs Tue Apr 19 04:07
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:17
python                 goscuter pts/2      0.13 secs Tue Apr 19 04:17
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:17
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:17
python                 goscuter pts/2      0.14 secs Tue Apr 19 04:17
cron             SF    root     __         0.00 secs Tue Apr 19 04:17
sh               S     root     __         0.00 secs Tue Apr 19 04:17
run-parts              root     __         0.00 secs Tue Apr 19 04:17
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:16
grep                   goscuter pts/2      0.00 secs Tue Apr 19 04:16
ps                     goscuter pts/2      0.01 secs Tue Apr 19 04:16
uname                  goscuter pts/2      0.00 secs Tue Apr 19 04:15
udisks-helper-a  S     root     __         0.00 secs Tue Apr 19 04:14
kworker/6:3       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/6:1       F    root     __         0.00 secs Tue Apr 19 01:14
kworker/2:3       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/2:2       F    root     __         0.00 secs Tue Apr 19 04:09
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 04:03
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 04:02
lastcomm               goscuter pts/2      0.00 secs Tue Apr 19 04:11
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:10
dir                    goscuter pts/2      0.00 secs Tue Apr 19 04:10
dir                    goscuter pts/2      0.00 secs Tue Apr 19 04:10
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:10
python                 goscuter pts/2      0.14 secs Tue Apr 19 04:10
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:09
info             S   X root     pts/2      0.01 secs Tue Apr 19 04:09
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:09
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:09
python                 goscuter pts/2      0.15 secs Tue Apr 19 04:09
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:09
tty              S     root     pts/2      0.00 secs Tue Apr 19 04:09
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:09
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:09
python                 goscuter pts/2      0.14 secs Tue Apr 19 04:09
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
kworker/4:0       F    root     __         0.00 secs Tue Apr 19 03:58
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:08
python                 goscuter pts/2      0.12 secs Tue Apr 19 04:08
tty                    goscuter pts/2      0.00 secs Tue Apr 19 04:08
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:07
kill             S     root     pts/2      0.00 secs Tue Apr 19 04:07
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:07
kill             S     root     pts/2      0.00 secs Tue Apr 19 04:07
bash              F    goscuter pts/2      0.00 secs Tue Apr 19 04:07
python                 goscuter pts/2      0.13 secs Tue Apr 19 04:07
kworker/0:3       F    root     __         0.00 secs Tue Apr 19 03:57
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:07
kill             S     root     pts/2      0.00 secs Tue Apr 19 04:07
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:06
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:06
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:05
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:05
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:05
last                   goscuter pts/2      0.00 secs Tue Apr 19 04:05
kworker/4:3       F    root     __         0.00 secs Tue Apr 19 03:52
uptime                 goscuter pts/2      0.00 secs Tue Apr 19 04:03
ac                     goscuter pts/2      0.00 secs Tue Apr 19 04:03
uptime                 goscuter pts/2      0.00 secs Tue Apr 19 04:03
ac                     goscuter pts/2      0.00 secs Tue Apr 19 04:02
kworker/0:0       F    root     __         0.00 secs Tue Apr 19 03:52
ac                     goscuter pts/2      0.00 secs Tue Apr 19 04:02
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:01
ac               S     root     pts/2      0.00 secs Tue Apr 19 04:01
apt-check              goscuter __         0.47 secs Tue Apr 19 04:01
sh                     goscuter __         0.00 secs Tue Apr 19 04:01
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:01
sh                     goscuter __         0.00 secs Tue Apr 19 04:01
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:01
sh                     goscuter __         0.00 secs Tue Apr 19 04:01
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:01
sh                     goscuter __         0.00 secs Tue Apr 19 04:01
dpkg                   goscuter __         0.00 secs Tue Apr 19 04:01
lsb_release            goscuter __         0.02 secs Tue Apr 19 04:01
ac                     goscuter pts/2      0.00 secs Tue Apr 19 04:00
sudo             S     root     pts/2      0.00 secs Tue Apr 19 04:00
apt-get          S     root     pts/2      0.26 secs Tue Apr 19 04:00
apt-get           F    root     pts/2      0.00 secs Tue Apr 19 04:00
sh                     root     pts/2      0.00 secs Tue Apr 19 04:00
touch                  root     pts/2      0.00 secs Tue Apr 19 04:00
dpkg             S     root     pts/0      0.08 secs Tue Apr 19 04:00
acct.postinst          root     pts/0      0.00 secs Tue Apr 19 04:00
invoke-rc.d            root     pts/0      0.00 secs Tue Apr 19 04:00
acct                   root     pts/0      0.00 secs Tue Apr 19 04:00
accton           S     root     pts/0      0.00 secs Tue Apr 19 04:00

```Seriously? So much nonsense. I had a really good feeling about the mistaken ~$ halt when my PC started going crazy with scripts whilst it was rebooting. Only to see a psuedo me is tying out commands on a terminal that isn't on my computer (I just flicked back manually through my commands - they match what I said above. 

halt
last
last
last
sudo last
last 

That's my commands. lol. Seems like I have a problem, that should be easily answered. But that has not been my experience, in the last 2 months. fml  

I like ubuntu and people on this forum seem cool, but for answers to stuff, where can I get them? I'm not a freeloader, I have $. 

So far, every Linux 'expert' I've paid has been an insulting, patronising, LYING moron. I got a champion guy on Launchpad helping me now and he's the first person who's expressly assisted in 2 months who seems like he has an IQ over 100. [I]Note: Maybe 80 have expressly assisted, many of them paid. 
[/I] 
Anyone know where I can find someone who **REALLY **actually knows Linux? I mean, we're talking open source code here right? :confused:
Why the heck are you asking these questions. (No offense, but STUPID questions). What, are all these things bothering you? Are they affecting your system or your life that shouldn't really be brought up here? IF yes, try Mac or something, because you are wasting server space.

---

### Post by Kururu Souchou on 2011-04-19
> **wojox said:**
> 26 hours in a day. That's classic. You have much to learn young grasshopper. :P

yes, stupid grasshopper

---

### Post by yetiman64 on 2011-04-19
> Only offensive people get offended, Sir I realize this is a response to another poster, but it is also a good indication to your attitude (read your thread title carefully again and think about others here who give up their free time to help you and others here who need it). You indicate in your 1st post you are joking, when to anyone helping here it is blatantly obvious you are ranting.

I for one was offended by this thread (mostly by, but not limited to the title). Apparently I am an offensive person, hmmmm :-k. I'm so offensive that I have dropped the past 7 drafts (all prior to drs305's post) in reply to this insulting thread, as I WOULD have been infracted myself.

Good luck in trying to get help here, you will need it. Please give serious consideration to the link in post #9, it may suit your needs better.

---

### Post by GWBouge on 2011-04-19
Ok, this is a bit against my better judgement, but it's pretty comical, so I'll chime in.  Only to this part for now, though:

> **goscuter1 said:**
> Ah okay, thanks. You might have clarified something for me...I'm still pretty confused though. Because I was wrong, it wasn't recursion going on. I went all the way to the end. So I just have a heck of a lot of desktop-environments to go with all those TTYs?

Of course, everyone (including me) should have noticed that the **files** in the screenshot I posted were not symbolic links. Those are actual files, repeated in every one of the 30 or w/e X11 folders. The clue (which I also missed) is in the little arrow on some, and not on others.  You can take another look, or here is another image of the "end" of the X11 chain. What that [ executable is, I wouldn't mind knowing.

Do this:

```
$ cd ~/Downloads
$ ln -s ~/Downloads ./Downloads
```

See that?  It makes a symlink in the folder you're symlinking.  Browse it.  Yes, it appears to have an 'end', and if you keep typing 'cd Downloads' in the terminal, it will eventually go back to ~/Downloads.  And no, the files don't have the symlink style icon.

... see where I'm going with this?  Talking about how high your computer literacy and IQ is (at which, yes, you come across as **very** rude and condescending) when you don't even know this kind of stuff isn't going to find you a whole lot of help.  Do what others have said, go back to the beginning, and find out how stuff works before you start finding 'problems' ...

---

### Post by matt_symes on 2011-04-19
Hmmmm.

```
matthew@matthew-laptop:~/Downloads$ ls /usr/bin/X11 -l
lrwxrwxrwx 1 root root 1 2011-04-08 02:15 /usr/bin/X11 -> .
matthew@matthew-laptop:~/Downloads$ 
```

```
matthew@matthew-laptop:~/Downloads$ file /usr/bin/[
/usr/bin/[: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
matthew@matthew-laptop:~/Downloads$
``` 

To know what the above file does, read up on shell scripting.

That's plenty from me. After all, i'm dumb :(

---

### Post by uRock on 2011-04-19
> **drs305 said:**
> This thread is in a support forum and is being monitored by the staff; **everyone** please stick to the technical issues or the thread will be closed.

It seems this was missed.

Thread Closed.

---

