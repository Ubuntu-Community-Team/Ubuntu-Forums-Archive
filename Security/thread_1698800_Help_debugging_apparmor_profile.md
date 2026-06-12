---
title: "Help debugging apparmor profile"
date: 2011-03-02
forum: Security
---

### Post by DanneStrat on 2011-03-02
Hi!

I've been spending some time on this forum

helping others, but now I found myself

in need for some help.;)


I want to confine transmission with an apparmor

profile and for that I have used bodhi.zazens

transmission profile to at least get started writing a profile.


As I can see in the profile, I have read and write

permissions to my "~/Downloads" folder. If I try to put

the profile to enforce mode, I get a "permission denied"

message when transmission try to access "~/Downloads".


I kept a terminal open with "/var/log/messages" during the 

test run of transmission (in complain mode). 


Both the log and profile are included in the attachment.

I would be very thankful if somebody could look at the log

and see what needs to be added to the profile.


I'm still learning apparmor, so if you could give

some info why we add certain things to the profile it would be 

great!


Thanks.

---

### Post by DanneStrat on 2011-03-03
[SIZE=2]Here is only the relevant info

extracted from the log so it's

much easier to see what access was denied:
[/SIZE]
[SIZE=2]
[/SIZE]```
[SIZE=2][FONT=&quot]denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"[/FONT][/SIZE]
[SIZE=2]
[/SIZE][SIZE=2][FONT=&quot]denied_mask="::r" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"[/FONT][/SIZE]
[SIZE=2]
[/SIZE][SIZE=2][FONT=&quot]denied_mask="::mr" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"[/FONT][/SIZE]
[SIZE=2]
[/SIZE][SIZE=2][FONT=&quot]denied_mask="::r" fsuid=1000 ouid=0 name="/usr/bin/xdg-open"[/FONT][/SIZE]
[SIZE=2][FONT=&quot]
denied_mask="::x" fsuid=1000 ouid=0 name="/usr/bin/gnome-open" 
[/FONT][/SIZE]
[SIZE=2][FONT=&quot]denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"[/FONT][/SIZE]
[SIZE=2]
[/SIZE][SIZE=2][FONT=&quot]denied_mask="::r" fsuid=1000 ouid=0 name="/usr/lib/libgnome-2.so.0.3000.0"[/FONT][/SIZE]
[SIZE=2]
[/SIZE][SIZE=2][FONT=&quot]denied_mask="::mr" fsuid=1000 ouid=0 name="/usr/lib/libgnome-2.so.0.3000.0"[/FONT][/SIZE]
[SIZE=2]
[/SIZE][SIZE=2][FONT=&quot]denied_mask="::r" fsuid=1000 ouid=0 name="/usr/lib/libgio-2.0.so.0.2400.1"[/FONT][/SIZE]

```[SIZE=2]
[/SIZE]
[SIZE=2]Anyone got any ideas what to add in the profile?

The apparmor profile I'm using is here:

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.bin.transmission](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.bin.transmission)
[/SIZE]

---

### Post by bodhi.zazen on 2011-03-03
That output is telling you exactly what you need to add to the profile.

Using the first message :

> denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"


you would add

/etc/ld.so.cache r,

and on ...

---

### Post by DanneStrat on 2011-03-03
> **bodhi.zazen said:**
> That output is telling you exactly what you need to add to the profile.

Using the first message :



you would add

/etc/ld.so.cache r,

and on ...

Alright, thank you for your answer!

I thought I was supposed to do that

but I wasn't completely sure so I felt it was 

better to ask first.

Thanks again!

---

### Post by DanneStrat on 2011-03-18
Now I finally had the time to finish my

profile and I'm really close(it needs some final touches).

I have only one denial left to deal

with in the logs.

This is what the profile looks like:

```
# Last Modified: Fri Mar 18 23:04:07 2011
#include <tunables/global>

/usr/bin/transmission flags=(complain) {
  #include <abstractions/base>

#include <abstractions/private-files>
  audit deny @{HOME}/.ssh/ mrwkl,
  audit deny @{HOME}/.ssh/** mrwkl,
  audit deny @{HOME}/.gnome2_private/ mrwkl,
  audit deny @{HOME}/.gnome2_private/** mrwkl,


network inet,

  

  owner /home/*/ r,
  owner /home/*/** r,
  owner /home/*/.cache/transmission/** r,
  owner /home/*/.config/gtk-2.0/gtkfilechooser.ini** rw,
  owner /home/*/.config/transmission/lock rwk,
  owner /home/*/.config/transmission/** rw,
  owner /home/*/.config/user-dirs.dirs r,
  owner /home/*/.gtk-bookmarks r,
  owner /home/*/.icons/** r,
  owner /home/*/.local/share/gvfs-metadata/home* r,
  owner /home/*/.local/share/Trash/files/** w,
  owner /home/*/.local/share/Trash/info/** rw,
  owner /home/*/.local/share/applications/defaults.list r,
  owner /home/*/.local/share/gvfs-metadata/ r,
  owner /home/*/.recently-used** rw,
  owner /home/*/Hämtningar/Transmission/ rw,
  owner /home/*/Hämtningar/Transmission/** rw,
  owner /home/*/Skrivbord/ rw,
  owner /home/*/Skrivbord/** rw,
  @{PROC}/*/fd/ r,
  @{PROC}/*/mounts r,
  
  /etc/fonts/** r,
  /etc/gai.conf r,
  /etc/gnome/defaults.list r,
  /etc/group r,
  /etc/host.conf r,
  /etc/hosts r,
  /etc/ld.so.cache r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /etc/resolv.conf r,
  /tmp/orbit-daniel/linc* w,
  /usr/bin/nautilus rix,
  /usr/bin/transmission rix,
  /usr/bin/xdg-open rix,
  /usr/lib/* r,
  /usr/lib/pango/1.6.0/modules/pango-basic-fc.so m,
  /usr/share/** r,
  /var/cache/** r,
  /var/lib/defoma/fontconfig.d/fonts.conf r,
  /var/run/gdm/** r,

}
```

and this is the denial I get:

```
 apparmor="ALLOWED" operation="open" parent=1 profile="/usr/bin/transmission" name="/home/" pid=7655 comm="transmission" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

I have granted access to "/home" in my profile.

When I test transmission in enforce mode, I also get

a message that access to "/home" was denied.

What should I add to the profile?

Thanks.

---

### Post by bodhi.zazen on 2011-03-19
/home != /home/your_user_name

Try adding

/home r,

---

### Post by DanneStrat on 2011-03-19
> **bodhi.zazen said:**
> /home != /home/your_user_name

Try adding

/home r,

Thanks.

I tried to add that to the profile

but I still get the same denial.

The profile looks like this now:

```
# Last Modified: Fri Mar 18 23:04:07 2011
#include <tunables/global>

/usr/bin/transmission flags=(complain) {
  #include <abstractions/base>

#include <abstractions/private-files>
  audit deny @{HOME}/.ssh/ mrwkl,
  audit deny @{HOME}/.ssh/** mrwkl,
  audit deny @{HOME}/.gnome2_private/ mrwkl,
  audit deny @{HOME}/.gnome2_private/** mrwkl,


network inet,

  
  owner /home/ r,
  owner /home/** r,
  owner /home/*/.cache/transmission/** r,
  owner /home/*/.config/gtk-2.0/gtkfilechooser.ini** rw,
  owner /home/*/.config/transmission/lock rwk,
  owner /home/*/.config/transmission/** rw,
  owner /home/*/.config/user-dirs.dirs r,
  owner /home/*/.gtk-bookmarks r,
  owner /home/*/.icons/** r,
  owner /home/*/.local/share/gvfs-metadata/home* r,
  owner /home/*/.local/share/Trash/files/** w,
  owner /home/*/.local/share/Trash/info/** rw,
  owner /home/*/.local/share/applications/defaults.list r,
  owner /home/*/.local/share/gvfs-metadata/ r,
  owner /home/*/.recently-used** rw,
  owner /home/*/Hämtningar/Transmission/** rw,
  owner /home/*/Skrivbord/** rw,
  /proc/*/fd/ r,
  /proc/*/mounts r,
  
  /etc/fonts/** r,
  /etc/gai.conf r,
  /etc/gnome/defaults.list r,
  /etc/group r,
  /etc/host.conf r,
  /etc/hosts r,
  /etc/ld.so.cache r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /etc/resolv.conf r,
  /tmp/orbit-daniel/linc* w,
  /usr/bin/nautilus rix,
  /usr/bin/transmission rix,
  /usr/bin/xdg-open rix,
  /usr/lib/* r,
  /usr/lib/pango/1.6.0/modules/pango-basic-fc.so m,
  /usr/share/** r,
  /var/cache/** r,
  /var/lib/defoma/fontconfig.d/fonts.conf r,
  /var/run/gdm/** r,

}

```

---

### Post by DanneStrat on 2011-03-19
I'm also wondering what does "owner" before "/home/" do? 

Is it really needed?

---

### Post by bodhi.zazen on 2011-03-19
> **DanneStrat said:**
> I'm also wondering what does "owner" before "/home/" do? 

Is it really needed?

owner before /home means you are giveing read access only to the owner of the /home directory.

/home is owned by root, as are other system files such as /etc/* , so no you just want 

/home

not

owner /home

I use "owner" to restrict access in /home/user to the user owning the home directory.

Thus when you run transmission as user1 you can not affect files in user2's home. 

So user1 when running firefox does not have access to /home/user2/.mozilla for example.

HTH

---

### Post by DanneStrat on 2011-03-19
> **bodhi.zazen said:**
> owner before /home means you are giveing read access only to the owner of the /home directory.

/home is owned by root, as are other system files such as /etc/* , so no you just want 

/home

not

owner /home

I use "owner" to restrict access in /home/user to the user owning the home directory.

Thus when you run transmission as user1 you can not affect files in user2's home. 

So user1 when running firefox does not have access to /home/user2/.mozilla for example.

HTH

That fixed it.

Thanks man!

---

### Post by DanneStrat on 2011-03-22
I posted my profile in the

"share your apparmor profiles" thread:

[http://ubuntuforums.org/showthread.php?p=6353911](http://ubuntuforums.org/showthread.php?p=6353911)

---

