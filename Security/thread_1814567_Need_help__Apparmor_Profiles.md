---
title: "Need help || Apparmor Profiles"
date: 2011-07-29
forum: Security
---

### Post by linuxyogi on 2011-07-29
Hi,

I am using FF ver 5.0.1 from [here]("http://download.mozilla.org/?product=firefox-5.0.1&os=linux&lang=en-US")

After reading [http://ubuntuforums.org/showpost.php?p=6353900&postcount=4](http://ubuntuforums.org/showpost.php?p=6353900&postcount=4)

I did ```
sudo aa-logprof /path to firefox
```Allowed all when asked. But when I try to start FF in enforce mode I get 


```
$ /home/tux/.firefox/firefox
/home/tux/.firefox/firefox: 60: basename: Permission denied
exec: 139: /home/tux/.firefox/run-mozilla.sh: Permission denied

```

This is the profile 

```
# Last Modified: Sat Jul 30 02:16:27 2011
#include <tunables/global>

/home/tux/.firefox/firefox flags=(complain) {
  #include <abstractions/apache2-common>
  #include <abstractions/base>


  deny owner "/home/tux/Desktop/&#8234;Harsha Bhogle on the 1st Test Match between India and England, at Lord's&#8236;&#8207; - YouTube.flv" w,

  /bin/dash ix,
  owner /home/*/.firefox/firefox r,
  owner /home/*/.mozilla/firefox/4w442atz.default/adblockplus/cache.js w,
  owner /home/*/.mozilla/firefox/4w442atz.default/adblockplus/patterns.ini w,
  owner /home/*/.mozilla/firefox/4w442atz.default/adblockplus/patterns.ini-temp rw,
  owner /home/*/.mozilla/firefox/4w442atz.default/places.sqlite-shm k,
  owner /home/*/.mozilla/firefox/4w442atz.default/prefs.js r,
  /proc/meminfo r,
  /usr/bin/dirname rix,
  /usr/share/fonts/** r,
  /usr/share/icons/Humanity/actions/16/document-save-as.svg r,
  /usr/share/icons/Humanity/actions/16/go-home.svg r,
  /usr/share/icons/Humanity/actions/16/go-next.svg r,
  /usr/share/icons/Humanity/actions/16/go-previous.svg r,


```What do I need to change ?

---

### Post by bodhi.zazen on 2011-07-29
Firefox is a big application to write a profile for.

I see firefox is in complain mode. go ahead and use firefox for a bit, go to a few web sites, use flash, etc.

Then close firefox and run aa-logprof

Then put your profile into enforcing mode and try some more.

Alternately you can look at another firefox profile as a template.

See the apparmor sticky [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

And also:

[http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/](http://blog.bodhizazen.net/linux/apparmor-privoxy-profile/)

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.10/usr.bin.firefox](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.10/usr.bin.firefox)

---

### Post by linuxyogi on 2011-07-29
[[COLOR=#980101]**@bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")

Hi,

[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")```
$ sudo aa-logprof 
[sudo] password for tux: 
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.

Profile:  /home/tux/.firefox/firefox
Execute:  /usr/bin/basename
Severity: unknown


(I)nherit / (P)rofile / (C)hild / (N)ame / (U)nconfined / (X)ix / (D)eny / Abo(r)t / (F)inish
```

^ This appears at the begining of aa-logprof. Which option should I choose ? I tried both (P)rofile & (I)nherit.

---

### Post by linuxyogi on 2011-07-29
@Bodhi.Zazen

I am atm using FF in complain mode. I am trying read those links, this I guess is going to take some time.

In the mean time I have created a profile for Chromium browser & using it in enforce mode.

[http://dl.dropbox.com/u/30630174/aa%20profile](http://dl.dropbox.com/u/30630174/aa%20profile)

> [FONT=Times New Roman]Rules for files include  [<<<]("http://ubuntuforums.org/showpost.php?p=6353899&postcount=3")

 	Code:
 	r = read w = write l = link k = lock a = append 
[/FONT]


This is the profile for Chromium

```


# Last Modified: Sat Jul 30 06:22:31 2011
#include <tunables/global>

/usr/bin/chromium-browser {
  #include <abstractions/base>



  /bin/dash ix,
  /bin/readlink rix,
  /etc/chromium-browser/default r,
  /etc/lsb-release r,
 [COLOR=Red] /home/tux/ r,[/COLOR]
  /proc/meminfo r,
  /usr/bin/chromium-browser r,
  /usr/lib/chromium-browser/chromium-browser px,

}

```


Now r=read [COLOR=Black]& the the profile is in enforce mode, but I can still save file in /home/tux. 

Is apparmor suppose to not let that happen ? [/COLOR]

---

### Post by bodhi.zazen on 2011-07-29
> **linuxyogi said:**
> @Bodhi.Zazen

I am atm using FF in complain mode. I am trying read those links, this I guess is going to take some time.

In the mean time I have created a profile for Chromium browser & using it in enforce mode.

[http://dl.dropbox.com/u/30630174/aa%20profile](http://dl.dropbox.com/u/30630174/aa%20profile)




This is the profile for Chromium

```


# Last Modified: Sat Jul 30 06:22:31 2011
#include <tunables/global>

/usr/bin/chromium-browser {
  #include <abstractions/base>



  /bin/dash ix,
  /bin/readlink rix,
  /etc/chromium-browser/default r,
  /etc/lsb-release r,
 [COLOR=Red] /home/tux/ r,[/COLOR]
  /proc/meminfo r,
  /usr/bin/chromium-browser r,
  /usr/lib/chromium-browser/chromium-browser px,

}

```


Now r=read [COLOR=Black]& the the profile is in enforce mode, but I can still save file in /home/tux. 

Is apparmor suppose to not let that happen ? [/COLOR]

As I indicated in my first post, browsers are complex and not the best place to start. I highly suggest you start with an easier program (like privoxy).

Second, did you reload your apparmor profile for chromium ?

What is the output of

```
aa-status
```

---

### Post by linuxyogi on 2011-07-30
> **bodhi.zazen said:**
> As I indicated in my first post, browsers are complex and not the best place to start. I highly suggest you start with an easier program (like privoxy).

Second, did you reload your apparmor profile for chromium

What is the output of

```
aa-status
```


Yes, I did  
```
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.chromium-browser 
``` also 

tried ```
 sudo /etc/init.d/apparmor reload
```.


```
$ sudo aa-status
[sudo] password for tux: 
apparmor module is loaded.
40 profiles are loaded.
11 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/chromium-browser
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
29 profiles are in complain mode.
   /bin/ping
   /home/tux/.firefox/firefox
   /home/tux/.firefox/firefox//null-25
   /home/tux/.firefox/firefox//null-25//null-26
   /home/tux/.firefox/firefox//null-25//null-27
   /home/tux/.firefox/firefox//null-25//null-28
   /home/tux/.firefox/firefox//null-25//null-29
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/bin/basename
   /usr/bin/expr
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
5 processes have profiles defined.
2 processes are in enforce mode :
   /sbin/dhclient3 (1753) 
   /usr/sbin/cupsd (1097) 
3 processes are in complain mode.
   /home/tux/.firefox/firefox//null-25//null-29 (1720) 
   /usr/sbin/avahi-daemon (814) 
   /usr/sbin/avahi-daemon (812) 
0 processes are unconfined but have a profile defined.


```

---

### Post by bodhi.zazen on 2011-07-30
I do not see chromium on the list, although I see the chromium profile listed as being in enforce mode.

At any rate, for what it is worth, here is the profile I used for chromium in Ubuntu 10.04

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser)

---

### Post by linuxyogi on 2011-07-30
> **bodhi.zazen said:**
> I do not see chromium on the list, although I see the chromium profile listed as being in enforce mode.


What do you think went wrong ?  I actually tried aa-enforce multiple times but same thing.


> **bodhi.zazen said:**
> 

At any rate, for what it is worth, here is the profile I used for chromium in Ubuntu 10.04

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.lib.chromium-browser.chromium-browser)

Thanks. I will try that once this problem is solved.

---

### Post by bodhi.zazen on 2011-07-30
I think the profile needs to be pointed at the lib and not the binary.

usr.lib.chromium-browser.chromium-browser

But my recollection is chromium was tricky as it uses a sandbox.

---

### Post by linuxyogi on 2011-07-30
Finally FF starts when only when 1/2 profiles is in enforce mode, namely the "home.tux..firefox.firefox" but when I FF fails to start when "home.tux..firefox.run-mozilla.sh " is in enforce mode.
```
$apparmor module is loaded.
110 profiles are loaded.
13 profiles are in enforce mode.
   /home/tux/.firefox/firefox
   /home/tux/.firefox/run-mozilla.sh
   /sbin/dhclient3
   /usr/bin/chromium-browser
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
97 profiles are in complain mode.
   /bin/ping
   /home/tux/.firefox/run-mozilla.sh//null-64
   /home/tux/.firefox/run-mozilla.sh//null-65
   /home/tux/.firefox/run-mozilla.sh//null-66
   /home/tux/.firefox/run-mozilla.sh//null-66//null-67
   /home/tux/.firefox/run-mozilla.sh//null-66//null-68
   /home/tux/.firefox/run-mozilla.sh//null-66//null-69
   /home/tux/.firefox/run-mozilla.sh//null-66//null-6a
   /home/tux/.firefox/run-mozilla.sh//null-66//null-6b
   /home/tux/.firefox/run-mozilla.sh//null-66//null-6c
   /home/tux/.firefox/run-mozilla.sh//null-66//null-6d
   /home/tux/.firefox/run-mozilla.sh//null-66//null-6e
   /home/tux/.firefox/run-mozilla.sh//null-66//null-6f
   /home/tux/.firefox/run-mozilla.sh//null-66//null-70
   /home/tux/.firefox/run-mozilla.sh//null-66//null-71
   /home/tux/.firefox/run-mozilla.sh//null-66//null-72
   /home/tux/.firefox/run-mozilla.sh//null-66//null-73
   /home/tux/.firefox/run-mozilla.sh//null-66//null-74
   /home/tux/.firefox/run-mozilla.sh//null-66//null-75
   /home/tux/.firefox/run-mozilla.sh//null-66//null-76
   /home/tux/.firefox/run-mozilla.sh//null-66//null-77
   /home/tux/.firefox/run-mozilla.sh//null-66//null-78
   /home/tux/.firefox/run-mozilla.sh//null-66//null-79
   /home/tux/.firefox/run-mozilla.sh//null-66//null-7a
   /home/tux/.firefox/run-mozilla.sh//null-66//null-7b
   /home/tux/.firefox/run-mozilla.sh//null-66//null-7c
   /home/tux/.firefox/run-mozilla.sh//null-66//null-7d
   /home/tux/.firefox/run-mozilla.sh//null-66//null-7e
   /home/tux/.firefox/run-mozilla.sh//null-66//null-7f
   /home/tux/.firefox/run-mozilla.sh//null-66//null-80
   /home/tux/.firefox/run-mozilla.sh//null-66//null-81
   /home/tux/.firefox/run-mozilla.sh//null-66//null-82
   /home/tux/.firefox/run-mozilla.sh//null-66//null-83
   /home/tux/.firefox/run-mozilla.sh//null-66//null-84
   /home/tux/.firefox/run-mozilla.sh//null-66//null-85
   /home/tux/.firefox/run-mozilla.sh//null-66//null-86
   /home/tux/.firefox/run-mozilla.sh//null-66//null-87
   /home/tux/.firefox/run-mozilla.sh//null-66//null-88
   /home/tux/.firefox/run-mozilla.sh//null-66//null-89
   /home/tux/.firefox/run-mozilla.sh//null-66//null-8a
   /home/tux/.firefox/run-mozilla.sh//null-66//null-8b
   /home/tux/.firefox/run-mozilla.sh//null-66//null-8c
   /home/tux/.firefox/run-mozilla.sh//null-66//null-8d
   /home/tux/.firefox/run-mozilla.sh//null-66//null-8e
   /home/tux/.firefox/run-mozilla.sh//null-66//null-8f
   /home/tux/.firefox/run-mozilla.sh//null-66//null-90
   /home/tux/.firefox/run-mozilla.sh//null-66//null-91
   /home/tux/.firefox/run-mozilla.sh//null-66//null-92
   /home/tux/.firefox/run-mozilla.sh//null-66//null-93
   /home/tux/.firefox/run-mozilla.sh//null-66//null-94
   /home/tux/.firefox/run-mozilla.sh//null-66//null-95
   /home/tux/.firefox/run-mozilla.sh//null-66//null-96
   /home/tux/.firefox/run-mozilla.sh//null-66//null-97
   /home/tux/.firefox/run-mozilla.sh//null-66//null-98
   /home/tux/.firefox/run-mozilla.sh//null-66//null-99
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/bin/basename
   /usr/bin/expr
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//null-9a
   /usr/lib/chromium-browser/chromium-browser//null-9b
   /usr/lib/chromium-browser/chromium-browser//null-9b//null-9c
   /usr/lib/chromium-browser/chromium-browser//null-9b//null-9d
   /usr/lib/chromium-browser/chromium-browser//null-9b//null-9e
   /usr/lib/chromium-browser/chromium-browser//null-9b//null-9f
   /usr/lib/chromium-browser/chromium-browser//null-9b//null-a0
   /usr/lib/chromium-browser/chromium-browser//null-9b//null-a1
   /usr/lib/chromium-browser/chromium-browser//null-9b//null-a2
   /usr/lib/chromium-browser/chromium-browser//null-a3
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-a5
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-a6
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-a7
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-a8
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-a9
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-aa
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-ab
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-ac
   /usr/lib/chromium-browser/chromium-browser//null-a3//null-a4//null-ac//null-ad
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
8 processes have profiles defined.
2 processes are in enforce mode :
   /sbin/dhclient3 (887) 
   /usr/sbin/cupsd (1117) 
6 processes are in complain mode.
   /usr/lib/chromium-browser/chromium-browser (3811) 
   /usr/lib/chromium-browser/chromium-browser (3809) 
   /usr/lib/chromium-browser/chromium-browser//null-9a (3813) 
   /usr/lib/chromium-browser/chromium-browser//null-9a (3862) 
   /usr/sbin/avahi-daemon (902) 
   /usr/sbin/avahi-daemon (903) 
0 processes are unconfined but have a profile defined.

```


```
# Last Modified: Sat Jul 30 23:05:58 2011
#include <tunables/global>

/home/tux/.firefox/firefox {
  #include <abstractions/apache2-common>
  #include <abstractions/base>


  deny owner "/home/tux/Desktop/&#8234;Harsha Bhogle on the 1st Test Match between India and England, at Lord's&#8236;&#8207; - YouTube.flv" w,

  /bin/dash ix,
  /etc/mailcap r,
  /etc/mime.types r,
  owner /home/*/.firefox/chrome/icons/default/default16.png r,
  owner /home/*/.firefox/chrome/icons/default/default32.png r,
  owner /home/*/.firefox/chrome/icons/default/default48.png r,
  owner /home/*/.firefox/firefox r,
  owner /home/*/.firefox/run-mozilla.sh r,
  /home/*/.firefox/run-mozilla.sh px,
  owner /home/*/.mozilla/firefox/4w442atz.default/NoScriptSTS.db w,
  owner /home/*/.mozilla/firefox/4w442atz.default/NoScriptSTS.db.tmp rw,
  owner /home/*/.mozilla/firefox/4w442atz.default/adblockplus/cache.js w,
  owner /home/*/.mozilla/firefox/4w442atz.default/adblockplus/patterns.ini w,
  owner /home/*/.mozilla/firefox/4w442atz.default/adblockplus/patterns.ini-temp rw,
  owner /home/*/.mozilla/firefox/4w442atz.default/bookmarkbackups/ r,
  owner /home/*/.mozilla/firefox/4w442atz.default/content-prefs.sqlite rwk,
  owner /home/*/.mozilla/firefox/4w442atz.default/cookies.sqlite wk,
  owner /home/*/.mozilla/firefox/4w442atz.default/downloads.sqlite rwk,
  owner /home/*/.mozilla/firefox/4w442atz.default/dta_queue.sqlite wk,
  owner /home/*/.mozilla/firefox/4w442atz.default/extensions/netvideohunter@netvideohunter.com/chrome/content/mediaList.xul r,
  owner /home/*/.mozilla/firefox/4w442atz.default/localstore-1.rdf rw,
  owner /home/*/.mozilla/firefox/4w442atz.default/localstore.rdf w,
  owner /home/*/.mozilla/firefox/4w442atz.default/permissions.sqlite wk,
  owner /home/*/.mozilla/firefox/4w442atz.default/places.sqlite wk,
  owner /home/*/.mozilla/firefox/4w442atz.default/places.sqlite-shm wk,
  owner /home/*/.mozilla/firefox/4w442atz.default/prefs-1.js rw,
  owner /home/*/.mozilla/firefox/4w442atz.default/prefs.js rw,
  owner /home/*/.mozilla/firefox/4w442atz.default/sessionstore-1.js w,
  owner /home/*/.mozilla/firefox/4w442atz.default/signons.sqlite rwk,
  owner /home/*/.mozilla/firefox/4w442atz.default/urlclassifierkey3.txt rw,
  owner /home/*/.mozilla/firefox/4w442atz.default/webappsstore.sqlite wk,
  owner /home/*/.recently-used.xbel r,
  /proc/meminfo r,
  owner /tmp/plugtmp/plugin-crossdomain.xml w,
  /usr/bin/basename px,
  /usr/bin/dirname rix,
  /usr/bin/expr px,
  /usr/share/fonts/** r,
  /usr/share/icons/DMZ-White/cursors/hand r,
  /usr/share/icons/Humanity/actions/16/document-open.svg r,
  /usr/share/icons/Humanity/actions/16/document-print-preview.svg r,
  /usr/share/icons/Humanity/actions/16/document-print.svg r,
  /usr/share/icons/Humanity/actions/16/document-properties.svg r,
  /usr/share/icons/Humanity/actions/16/document-save-as.svg r,
  /usr/share/icons/Humanity/actions/16/edit-copy.svg r,
  /usr/share/icons/Humanity/actions/16/edit-cut.svg r,
  /usr/share/icons/Humanity/actions/16/edit-delete.svg r,
  /usr/share/icons/Humanity/actions/16/edit-paste.svg r,
  /usr/share/icons/Humanity/actions/16/go-home.svg r,
  /usr/share/icons/Humanity/actions/16/go-next.svg r,
  /usr/share/icons/Humanity/actions/16/go-previous.svg r,
  /usr/share/icons/Humanity/actions/16/media-playback-pause.svg r,
  /usr/share/icons/Humanity/actions/16/media-playback-start.svg r,
  /usr/share/icons/Humanity/actions/16/process-stop.svg r,
  /usr/share/icons/Humanity/actions/16/system-shutdown.svg r,
  /usr/share/icons/Humanity/actions/16/view-refresh.svg r,
  /usr/share/icons/Humanity/actions/22/edit-undo.svg r,
  /usr/share/icons/Humanity/actions/24/go-next.svg r,
  /usr/share/icons/Humanity/actions/24/go-previous.svg r,
  /usr/share/icons/Humanity/places/16/folder.svg r,


```


```
# Last Modified: Sat Jul 30 23:05:59 2011
#include <tunables/global>

/home/tux/.firefox/run-mozilla.sh flags=(complain) {
  #include <abstractions/apache2-common>
  #include <abstractions/base>


  /bin/dash ix,
  owner /home/*/.firefox/run-mozilla.sh r,
  owner /home/*/.mozilla/firefox/4w442atz.default/adblockplus/patterns.ini-temp rw,
  owner /home/*/.mozilla/firefox/4w442atz.default/prefs.js r,
  owner /home/*/.mozilla/firefox/4w442atz.default/signons.sqlite k,
  /usr/bin/basename rix,

}

```




```
$ /home/tux/.firefox/firefox
/home/tux/.firefox/run-mozilla.sh: 39: dirname: Permission denied
/home/tux/.firefox/run-mozilla.sh: 312: uname: Permission denied
[: 312: !=: unexpected operator
exec: 392: /home/tux/.firefox/firefox-bin: Permission denied
```

---

### Post by bodhi.zazen on 2011-07-30
Well, next I advise you learn to "glob"

All your /usr/share/icons ....

can be replaced by a single line

/usr/share/icons/** r,

owner /home/*/ should be

owner @{HOME}/

keep reading.

I have posted several profiles for your review , in each of the profiles I posted are rules for how I manage "owner @{HOME}/"

---

### Post by linuxyogi on 2011-07-30
@Bodhi.Zazen

Please see my [edit ]("http://ubuntuforums.org/showpost.php?p=11102199&postcount=10")

Yes, FF is really too complicated to begin with. 

But I will keep on trying with another installation of FF (virtually?). Since I have started, dont wanna give up.

But since I use FF everyday I was thinking to secure it by copying one of your profiles. But I see two complications,

**1>** I am not using FF from the repos. I am using the precompiled version which is available for download at their site.

**2>**I am using 5.0.1

Have you written any profile which can be used with my FF installation ? 

All I wanna do is restrict FF's write permission to the /home/tux/Downloads folder. I learned that cant really restrict 
FF to just the Downloads folder coz it need to read other stuff within the home folder. Which seems to me as downside of apparmor. For in case FF is compromised it gets access to all my data.

---

### Post by bodhi.zazen on 2011-07-31
I took a look at it last night and sort of ran into the same dead end you did.

I wrote a profile using aa-genprof and never got to a point where I could confine firefox downloaded from mozilla and running from your home directory.

I am not sure of the problem and suggest you file a bug report on launchpad against apparmor.

You will need to decide which is more important, running firefox as you are or using firefox from the ubuntu repositories and using or modifying the default firefor apparmor profile.

If you wish to learn to use apparmor, once again start with simpler applications, look at the apparmor sticky, and learn the syntax.

I understand your frustration, but you are not exactly following my advice either. For example you are still using /home/* rather then the syntax I showed you and I can not see you looked at the profiles I showed you from my web site either. You are not using globbing and you have not incorporated any of the syntax I use for firefox and my home directory.

So you essentially have two problems:

1. You have not yet learned the basics of apparmor and you  are tring to confine a complex, custom application.

2. You are not following advice or examples.

Good luck to you.

---

### Post by bodhi.zazen on 2011-08-01
OK, here is the profile that is working for me. It may be more restrictive then you want ;)

profile name

/etc/apparmor.d/home.your_user.firefox.firefox

```
# Last Modified: Sat Jul 30 23:26:18 2011
#include <tunables/global>

/home/your_user/firefox/firefox {
  #include <abstractions/base>
  #include <abstractions/gnome>
  #include <abstractions/kde>
  #include <abstractions/nameservice>

  /bin/dash ix,
  /bin/uname rix,
  /etc/fstab r,
  @{HOME}/ r,
  @{HOME}/.config/** rw,
  @{HOME}/.kde/** r,
  @{HOME}/.mozilla/firefox/** rwk,
  @{HOME}/Downloads/** rw,
  @{HOME}/.Private/** rw,
  /home/your_user/firefox/** mrwixkl,

  @{PROC}/** r,

  /usr/bin/basename rix,
  /usr/bin/dirname rix,
  /usr/bin/expr rix,
  /usr/bin/kde4-config rix,
  /usr/share/** r,

  /usr/lib/mozilla/plugins/** rmixk,

}
```

With that profile flash is working. If you have problems, see the links to other firefox profiles I gave you earlier.

Note: .Private is needed with an encrypted home directory ;)

---

### Post by linuxyogi on 2011-08-01
After copying that profile I am getting the following

```
$ sudo apparmor_parser -r /etc/apparmor.d/home.tux..firefox.firefox 
failed user merge 0x814205 0x2204881
profile /home/tux/.firefox/firefox: has merged rule /usr/bin/kde4-config with multiple x modifiers
ERROR merging rules for profile /home/tux/.firefox/firefox, failed to load

```

So, cant test the profile ay my end yet.

---

### Post by bodhi.zazen on 2011-08-01
Delete that line "  /usr/bin/kde4-config rix,"

---

### Post by linuxyogi on 2011-08-01
> **bodhi.zazen said:**
> Delete that line "  /usr/bin/kde4-config rix,"

Deleted that line, FF starts, restrictions are working too. Awesome !!! :D  

But flash is not working atm. I added the following line from your profile you gave me.


```
#[code]# Last Modified: Sat Jul 30 23:26:18 2011
#include <tunables/global>

/home/tux/.firefox/firefox {
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/gnome>
  #include <abstractions/kde>
  #include <abstractions/nameservice>

  /bin/dash ix,
  /bin/uname rix,
  /etc/fstab r,
  @{HOME}/ r,
  @{HOME}/.config/** rw,
  @{HOME}/.kde/** r,
  @{HOME}/.mozilla/firefox/** rwk,
  @{HOME}/Downloads/** rw,
  /home/tux/.firefox/** mrwixkl,

  @{PROC}/** r,

  /usr/bin/basename rix,
  /usr/bin/dirname rix,
  /usr/bin/expr rix,
  /usr/share/** r,

  /usr/lib/mozilla/plugins/** rmixk,

[B]# Flash
  owner @{HOME}/.adobe/ rw,
  owner @{HOME}/.adobe/** rw,
  owner @{HOME}/.macromedia/ rw,
  owner @{HOME}/.macromedia/** rw,

# Allow flash to use video acceleration[/B] [B]
  /dev/nvidiactl rw, 
  /dev/nvidia0 rw,[/B]

}


```Closed FF
Added those lines
Did ```
 sudo apparmor_parser -r /etc/apparmor.d/home.tux..firefox.firefox 
```Started FF but flash is still not working.

```
$ dir /dev |grep nvidia
dsp         nvidia0         scd0     tty21    tty5   vcs1
dvd         nvidiactl         sda     tty22    tty50  vcs2
```

---

### Post by bodhi.zazen on 2011-08-01
What error message are you getting in the logs ?

---

### Post by linuxyogi on 2011-08-01
> **bodhi.zazen said:**
> What error message are you getting in the logs ?

```
Aug  2 02:07:02 tux kernel: [ 2613.999497] type=1503 audit(1312231022.974:5857):  operation="open" pid=3249 parent=1 profile="/home/tux/.firefox/firefox" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/proc/"
Aug  2 02:07:02 tux kernel: [ 2614.001084] type=1503 audit(1312231022.984:5858):  operation="open" pid=3217 parent=1 profile="/home/tux/.firefox/firefox" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tux/.mozilla/plugins/"

```

---

### Post by bodhi.zazen on 2011-08-01
The first you can ignore or if you wish add

```
@{PROC}/ r,
```

The second can be covered by

```
@{HOME}/.mozilla/** rwk,
```

or

```
@{HOME}/.mozilla/plugins/** rwk,
```

Your next lesson is to look at those logs and understand where I got those rules from.

---

### Post by linuxyogi on 2011-08-01
Added both the lines
```

#[code]# Last Modified: Sat Jul 30 23:26:18 2011
#include <tunables/global>

/home/tux/.firefox/firefox {
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/gnome>
  #include <abstractions/kde>
  #include <abstractions/nameservice>

  /bin/dash ix,
  /bin/uname rix,
  /etc/fstab r,
  **@{PROC}/ r,**
  @{HOME}/ r,
  @{HOME}/.config/** rw,
  @{HOME}/.kde/** r,
  @{HOME}/.mozilla/firefox/** rwk,
  @{HOME}/Downloads/** rw,
  /home/tux/.firefox/** mrwixkl,
  @{HOME}/.mozilla/** rwk,
 ** @{HOME}/.mozilla/plugins/** rwk,**
  
  

  @{PROC}/** r,

  /usr/bin/basename rix,
  /usr/bin/dirname rix,
  /usr/bin/expr rix,
  /usr/share/** r,

  /usr/lib/mozilla/plugins/** rmixk,

# Flash
  owner @{HOME}/.adobe/ rw,
  owner @{HOME}/.adobe/** rw,
  owner @{HOME}/.macromedia/ rw,
  owner @{HOME}/.macromedia/** rw,

# Allow flash to use video acceleration
  /dev/nvidiactl rw, 
  /dev/nvidia0 rw,


}
```

Now while trying play a video at youtube log says

```
Aug  2 07:47:07 tux kernel: [ 1188.398593] type=1503 audit(1312251427.386:1190):  operation="ptrace" pid=2312 parent=1 profile="/home/tux/.firefox/firefox" tracer=2312 tracee=1468
```


I actually tried adding 

```
@{HOME}/.mozilla/plugins/** rw
``` but didnt include "k". I read k means lock. I will definitely learn about in details. Then I got the /PROC. 

I am getting there ;-) .

But I dont know what to do about ptrace. Just guessing, need to add executable permission to @{PROC}/ r  ??.

I dont wanna experiment too much with this profile or I will mess it up. Once this gets solved I will start with something easy. Please suggest something other than Privoxy. I don't wanna write a profile for app which I don't use. But if you ask I will start with privoxy virtually.

---

### Post by bodhi.zazen on 2011-08-01
Take a look at the default apparmor profile included with Ubuntu (it is in apparmor-profiles), the firefox profiles I linked you on my web site, and tools such as aa-logprof

---

### Post by linuxyogi on 2011-08-04
> **bodhi.zazen said:**
> Take a look at the default apparmor profile included with Ubuntu (it is in apparmor-profiles), the firefox profiles I linked you on my web site, and tools such as aa-logprof

Consulted the default apparmor profile, your profiles, even logprof is offering nothing related to FF. 

I just configured FF in complain mode but flash player wont load (in complain mode too).

It was working fine before. 

I am using this addon [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Lastly I added the line /dev/zero m, & there was no real errors in the logs. Then decided to put FF in complain mode.

Everything is going haywire. :confused:

---

### Post by bodhi.zazen on 2011-08-05
If it does not work in complain mode, then it is a problem with flash and not apparmor.

---

### Post by linuxyogi on 2011-08-05
> **bodhi.zazen said:**
> If it does not work in complain mode, then it is a problem with flash and not apparmor.

Done !!! 

Deleted the aa profile for run.mozilla

Deleted the FF profile. (Not the aa profile)

Then added "m" to 

owner /home/*/.mozilla/plugins/libflashplayer.so r**m**,

Now flash works without any issues.

Thanks.

Please suggest an easy app other than Privoxy. 

Pidgin, Skype, Deluge, Google Earth ...etc

---

### Post by bodhi.zazen on 2011-08-05
> **linuxyogi said:**
> Done !!! 

Glad you got it working.


> Please suggest an easy app other than Privoxy. 

Pidgin, Skype, Deluge, Google Earth ...etc

Take your pick. Pidgin should de very straight forward as should deluge.

Not sure about Skype or Google Earth.

---

### Post by linuxyogi on 2011-08-05
> **bodhi.zazen said:**
> Glad you got it working.




Take your pick. Pidgin should de very straight forward as should deluge.

Not sure about Skype or Google Earth.

ATM working on Deluge. 

What is the reason behind only the profile going into enforce mode & not the process.

It happened with FF & now its the same with Deluge.

I did ```
sudo aa-genprof deluge
```. Then changed it to complain mode but log 

shows nothing related to Deluge. Also, aa-logprof too offers nothing.

---

### Post by bodhi.zazen on 2011-08-05
See man aa-genprof, this is how it works, it puts the profile into complain mode, then you exercise the program, then you tell genprof to write a profile.

See the blog I posted about an apparmor profile for privoxy ;)

---

### Post by MiniT on 2011-08-14
Yes, Firefox really is a tough one to start out with.  I started with the default/sleeping Firefox profile that came in my Mint(Ubuntu 10.10). and mixxed in some BHODI magic.  Thanks for all your hard work around here, dude.  The Fire Fox AA profile you have for Ubuntu 10.10 gave me crucial insight into my correcting and fixing process.

I don't think I would have been able to do it straight from whassitcalled - - - is it genprof helps to make the profile?  Yeah, no I have to have examples of the right way to do it because my way  -  well uneducated is ignorant.  :)

Learning alot!  Yall keep doing this out loud, hear?

Deluge is  a BT client?
Like Transmission?
That's my ultimate goal in using AppArmor : to make all the network facing organisms play nice together, and keep their hands to themselves.

Still kind of a question in my mind, since I am not the smartest or most experienced  :  
If I limit a program to only access/only have certain permissions, does that mean that someone using it only has those permissions/boundaries?  What if it is run as root?  Or if a program calls up my fenced-in program?  Surely the only case where AppArmor won't apply is if the prog is run as root?  Or even then?

hmm . .  .

Hey good luck yall, and good lookin out.

mini

---

### Post by linuxyogi on 2011-08-21
@ Bodhi Zazen

Hi, I have created profiles for Dropbox, PIdgin, Google Earth. 

ATM using them in enforce mode. Before sharing my Dropbox profile here I opened tyhe profile with LIbreoffice to find and replace /home/ with @{HOME}/ & replace my username with *.

But now, 

```
$ sudo apparmor_parser -r usr.bin.dropbox 
AppArmor parser error for usr.bin.dropbox in usr.bin.dropbox at line 1: Found unexpected character: '&#65533;'

```Cant find any missing comma at end of any line. Here's the profile



```
&#65279;# Last Modified: Sat Aug 20 11:34:47 2011
#include <tunables/global>

/usr/bin/dropbox {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/ubuntu-konsole>


  capability sys_ptrace,


  deny /etc/passwd r,

  /bin/dash rix,
  /bin/readlink ix,
  /bin/which rix,
  /etc/python2.6/sitecustomize.py r,
  owner @{HOME}/*/ r,
  owner @{HOME}/*/.config/autostart/dropbox.desktop w,
  owner @{HOME}/*/.dropbox-dist/ r,
  owner @{HOME}/*/.dropbox-dist/icons/hicolor/16x16/status/ r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/_ncrypt.so mr,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/__init__.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/cipher.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/dh.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/digest.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/rsa.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/ssl.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/x509.pyc r,
  owner @{HOME}/*/.dropbox-dist/netifaces-0.5-py2.5-linux-x86_64.egg/netifaces.so mr,
  owner @{HOME}/*/.dropbox/ r,
  @{HOME}/*/.dropbox/** rix,
  owner @{HOME}/*/.dropbox/config.db rwk,
  owner @{HOME}/*/.dropbox/config.db-journal rw,
  owner @{HOME}/*/.dropbox/dropbox.pid rwk,
  owner @{HOME}/*/.dropbox/filecache.db wk,
  owner @{HOME}/*/.dropbox/filecache.db-journal rw,
  owner @{HOME}/*/.dropbox/host.db w,
  owner @{HOME}/*/.dropbox/l/** rw,
  owner @{HOME}/*/.dropbox/sigstore.db rwk,
  owner @{HOME}/*/.dropbox/unlink.db rw,
  owner @{HOME}/*/.fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3 r,
  owner @{HOME}/*/.icons/ r,
  owner @{HOME}/*/.local/share/icons/hicolor/16x16/apps/ r,
  owner @{HOME}/*/.local/share/icons/hicolor/32x32/apps/ r,
  owner @{HOME}/*/.local/share/icons/hicolor/48x48/apps/ r,
  owner @{HOME}/*/Dropbox/.dropbox w,
  owner @{HOME}/*/Dropbox/.~216883113597249541HI w,
  owner @{HOME}/*/Dropbox/.~3945515783863310787HI w,
  owner @{HOME}/*/Dropbox/.~5397912888794637208HI w,
  owner @{HOME}/*/Dropbox/.~7317713414570696711HI w,
  owner @{HOME}/*/Dropbox/wallpapers/Mt.Kailash.jpg r,
  owner @{HOME}/*/Dropbox/wallpapers/hazel-0a.jpg r,
  owner @{HOME}/*/Dropbox/wallpapers/kar106a.jpg r,
  owner @{HOME}/*/Dropbox/wallpapers/mt-kailash.jpg r,
  owner @{HOME}/*/Dropbox/wallpapers/sonal-chauhan-7a.jpg r,
  owner "@{HOME}/*/Dropbox/wallpapers/sonam kapoor Hot.jpg" r,
  @{HOME}/*/.dropbox-dist/* rix,
  @{HOME}/*/.dropbox-dist/dropboxd rix,
  /proc/*/cmdline r,
  owner /proc/*/mounts r,
  /sbin/ldconfig rix,
  /sbin/ldconfig.real rix,
  /usr/bin/dirname ix,
  /usr/bin/dropbox rix,
  /usr/bin/gconftool-2 rix,
  /usr/bin/gnome-open rix,
  /usr/bin/nautilus rix,
  /usr/bin/objdump rix,
  /usr/bin/python2.6 ix,
  /usr/lib{,32,64}/** mr,
  /usr/local/lib/python2.6/dist-packages/ r,
  /usr/share/applications/dropbox.desktop r,
  /usr/share/applications/nautilus.desktop r,
  /usr/share/pyshared/PIL.pth r,
  /usr/share/pyshared/apport_python_hook.py r,
  /usr/share/pyshared/cairo/__init__.py r,
  /usr/share/pyshared/gtk-2.0/gio/__init__.py r,
  /usr/share/pyshared/gtk-2.0/glib/__init__.py r,
  /usr/share/pyshared/gtk-2.0/glib/option.py r,
  /usr/share/pyshared/gtk-2.0/gobject/__init__.py r,
  /usr/share/pyshared/gtk-2.0/gobject/constants.py r,
  /usr/share/pyshared/gtk-2.0/gobject/propertyhelper.py r,
  /usr/share/pyshared/gtk-2.0/gtk/__init__.py r,
  /usr/share/pyshared/gtk-2.0/gtk/_lazyutils.py r,
  /usr/share/pyshared/gtk-2.0/gtk/deprecation.py r,
  /usr/share/pyshared/pygst.pth r,
  /usr/share/pyshared/pygtk.py r,
  /usr/share/pyshared/zope.interface-3.5.3-nspkg.pth r,
  /usr/share/themes/Ambiance/gtk-2.0/gtkrc r,
  /usr/share/themes/Default/gtk-2.0-key/gtkrc r,

}

 
```^ WHich line has the error ?  Dunno which one is line 1.

Dont wanna modify the other profiles before finding out what went wrong while editing this one.

---

### Post by bodhi.zazen on 2011-08-21
The first line, "#include <tunables/global>" needs to go below the 

"/usr/bin/dropbox {" with the other includes.

Also you can consolidate

  owner @{HOME}/*/.dropbox-dist/ r,
  owner @{HOME}/*/.dropbox-dist/** r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/_ncrypt.so mr,
  owner @{HOME}/*/.dropbox-dist/netifaces-0.5-py2.5-linux-x86_64.egg/netifaces.so mr,

And why do you have a * in "@{HOME}/*/"

specify a directory rather then a * , you can {list,multiple,directories} if needed

---

### Post by linuxyogi on 2011-08-21
> **bodhi.zazen said:**
> The first line, "#include <tunables/global>" needs to go below the 

"/usr/bin/dropbox {" with the other includes.

Also you can consolidate

  ```
owner @{HOME}/*/.dropbox-dist/ r,
  owner @{HOME}/*/.dropbox-dist/** r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/_ncrypt.so mr,
  owner @{HOME}/*/.dropbox-dist/netifaces-0.5-py2.5-linux-x86_64.egg/netifaces.so mr,

And why do you have a * in "@{HOME}/*/"

specify a directory rather then a * , you can {list,multiple,directories} if needed
```


Hi, I just moved that line below but the "/usr/bin/dropbox" 

But still getting the error.

Now the profile looks like 

```




&#65279;# Last Modified: Sat Aug 20 11:34:47 2011


  /usr/bin/dropbox {
 
  #include <tunables/global>
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/ubuntu-konsole>


  capability sys_ptrace,


  deny /etc/passwd r,

  /bin/dash rix,
  /bin/readlink ix,
  /bin/which rix,
  /etc/python2.6/sitecustomize.py r,
  owner @{HOME}/*/ r,
  owner @{HOME}/*/.config/autostart/dropbox.desktop w,
  owner @{HOME}/*/.dropbox-dist/ r,
  owner @{HOME}/*/.dropbox-dist/icons/hicolor/16x16/status/ r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/_ncrypt.so mr,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/__init__.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/cipher.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/dh.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/digest.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/rsa.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/ssl.pyc r,
  owner @{HOME}/*/.dropbox-dist/ncrypt-0.6.4-py2.5-linux-x86_64.egg/ncrypt/x509.pyc r,
  owner @{HOME}/*/.dropbox-dist/netifaces-0.5-py2.5-linux-x86_64.egg/netifaces.so mr,
  owner @{HOME}/*/.dropbox/ r,
  @{HOME}/*/.dropbox/** rix,
  owner @{HOME}/*/.dropbox/config.db rwk,
  owner @{HOME}/*/.dropbox/config.db-journal rw,
  owner @{HOME}/*/.dropbox/dropbox.pid rwk,
  owner @{HOME}/*/.dropbox/filecache.db wk,
  owner @{HOME}/*/.dropbox/filecache.db-journal rw,
  owner @{HOME}/*/.dropbox/host.db w,
  owner @{HOME}/*/.dropbox/l/** rw,
  owner @{HOME}/*/.dropbox/sigstore.db rwk,
  owner @{HOME}/*/.dropbox/unlink.db rw,
  owner @{HOME}/*/.fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3 r,
  owner @{HOME}/*/.icons/ r,
  owner @{HOME}/*/.local/share/icons/hicolor/16x16/apps/ r,
  owner @{HOME}/*/.local/share/icons/hicolor/32x32/apps/ r,
  owner @{HOME}/*/.local/share/icons/hicolor/48x48/apps/ r,
  owner @{HOME}/*/Dropbox/.dropbox w,
  owner @{HOME}/*/Dropbox/.~216883113597249541HI w,
  owner @{HOME}/*/Dropbox/.~3945515783863310787HI w,
  owner @{HOME}/*/Dropbox/.~5397912888794637208HI w,
  owner @{HOME}/*/Dropbox/.~7317713414570696711HI w,
  owner @{HOME}/*/Dropbox/wallpapers/Mt.Kailash.jpg r,
  owner @{HOME}/*/Dropbox/wallpapers/hazel-0a.jpg r,
  owner @{HOME}/*/Dropbox/wallpapers/kar106a.jpg r,
  owner @{HOME}/*/Dropbox/wallpapers/mt-kailash.jpg r,
  owner @{HOME}/*/Dropbox/wallpapers/sonal-chauhan-7a.jpg r,
  owner "@{HOME}/*/Dropbox/wallpapers/sonam kapoor Hot.jpg" r,
  @{HOME}/*/.dropbox-dist/* rix,
  @{HOME}/*/.dropbox-dist/dropboxd rix,
  /proc/*/cmdline r,
  owner /proc/*/mounts r,
  /sbin/ldconfig rix,
  /sbin/ldconfig.real rix,
  /usr/bin/dirname ix,
  /usr/bin/dropbox rix,
  /usr/bin/gconftool-2 rix,
  /usr/bin/gnome-open rix,
  /usr/bin/nautilus rix,
  /usr/bin/objdump rix,
  /usr/bin/python2.6 ix,
  /usr/lib{,32,64}/** mr,
  /usr/local/lib/python2.6/dist-packages/ r,
  /usr/share/applications/dropbox.desktop r,
  /usr/share/applications/nautilus.desktop r,
  /usr/share/pyshared/PIL.pth r,
  /usr/share/pyshared/apport_python_hook.py r,
  /usr/share/pyshared/cairo/__init__.py r,
  /usr/share/pyshared/gtk-2.0/gio/__init__.py r,
  /usr/share/pyshared/gtk-2.0/glib/__init__.py r,
  /usr/share/pyshared/gtk-2.0/glib/option.py r,
  /usr/share/pyshared/gtk-2.0/gobject/__init__.py r,
  /usr/share/pyshared/gtk-2.0/gobject/constants.py r,
  /usr/share/pyshared/gtk-2.0/gobject/propertyhelper.py r,
  /usr/share/pyshared/gtk-2.0/gtk/__init__.py r,
  /usr/share/pyshared/gtk-2.0/gtk/_lazyutils.py r,
  /usr/share/pyshared/gtk-2.0/gtk/deprecation.py r,
  /usr/share/pyshared/pygst.pth r,
  /usr/share/pyshared/pygtk.py r,
  /usr/share/pyshared/zope.interface-3.5.3-nspkg.pth r,
  /usr/share/themes/Ambiance/gtk-2.0/gtkrc r,
  /usr/share/themes/Default/gtk-2.0-key/gtkrc r,

}
```Need to get rid of this error, then I will try n improve the profile.

---

### Post by linuxyogi on 2011-08-21
@Bodhi Zazen

I just noticed that sound id not working in FF with that profile in enforce mode. 

Sorry for being late. I was away from home. 

Log shows nothing related to FF.

Solved !!! Added the following to the profile

/dev/shm/** r,
/lib/** mr,
owner /home/*/.pulse/** drix,

But the dropbox profile is still erroneous.

---

