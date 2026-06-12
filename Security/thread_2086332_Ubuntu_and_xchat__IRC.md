---
title: "Ubuntu and xchat / IRC"
date: 2012-11-20
forum: Security
---

### Post by Marbsie on 2012-11-20
Hello all! This is my first post on the forums. I hope this is the right place to ask this. I tried to ask this question on the xchat forum but their registration process seems to be broken and I never got an activation email.


I basically just have what is probably a really stupid question to ask. Please keep in mind I am new to Ubuntu and I know virtually nothing about IRC. I downloaded xchat to basically check it out and see what it's like. I joined a channel called #mp3passion and noticed that I kept seeing the following in the main chat window:



Received a CTCP SLOTS 8 5 NOW 21 99 89625 152742 1584690316503 0 1457480239 179306 OmeNServE v2.60 from *username* (to #mp3passion)



Or sometimes it would look like:



Received a CTCP MP3 blahblahblah.mp3 from *username* (to #mp3passion)


*username* was different peoples names and not literally "*username*"



What does it mean by Received??? Is this just an event notification that's completely safe or is it actually automatically downloading potentially harmful files?

I can't imagine any software having such a security risk on by default, and I know I'm probably just being a paranoid noob but I would really like to know if this is a potential security threat or if my system might have been compromised.


Thank you for your time.

---

### Post by Ms. Daisy on 2012-11-20
This should answer your question about CTCP
[http://en.wikibooks.org/wiki/Downloading_Files_from_IRC/File_Server_%28fserve%29_Guide](http://en.wikibooks.org/wiki/Downloading_Files_from_IRC/File_Server_%28fserve%29_Guide)

I'm going way out on a limb: if the name of the channel is mp3passion then I would expect that the purpose of the channel is to (legally or illegally) share mp3 files. Ergo the point is to download & upload files.

You're not being paranoid at all. Personally I wouldn't download any kind of file from IRC unless I were looking for a reason to reinstall. Don't click on links either. I wouldn't share personal information of any kind. I find it good practice to assume that there's at least one malicious person lurking/active in every channel.

---

### Post by Marbsie on 2012-11-20
Thank you for your response.

I have already taken a look at that page in my searching to find an answer earlier today. Unfortunately it still doesn't explain why it said  "Received a CTCP SLOTS 8 5 NOW 21 99 89625" etc. as I wrote above.

I never initiated any download. I was only there because I was testing out xchat and it was a channel with a lot of users. It could have just as easily been a movie or soccer chat. :)

I guess my main problem here is what received means when I never agreed to or wanted to receive anything. I just joined a public channel and BOOM it suddenly tells me I'm receiving something. That should bother anyone who doesn't know what it means and I unfortunately still don't.

I'd like to think it's just some kind of mundane event notification but I won't know until someone familiar with IRC can verify what this is.

I won't be able to log into my email or anything else until I can get this resolved. :(

---

### Post by Hungry Man on 2012-11-20
This isn't directly relevant to your questionbut... I don't think xChat is update anymore, meaning it won't get security patches. Because of this you'll probably want to run it within Apparmor. I can't guarantee this profile works as it's a bit old but you can give it a try.

> 
# Last Modified: Mon May 14 02:51:29 2012
#include <tunables/global>

/usr/bin/xchat {
#include <abstractions/apache2-common>
#include <abstractions/base>


/etc/fonts/** r,
/etc/python2.7/sitecustomize.py r,
/home/*/.Xauthority r,
/home/*/.cache/dconf/user rw,
/home/*/.config/dconf/user r,
/home/*/.config/enchant/ r,
/home/*/.config/enchant/en_US.dic rwk,
/home/*/.config/enchant/en_US.exc rwk,
/home/*/.local/share/icons/ r,
/home/*/.local/share/icons/hicolor/**/ r,
/home/*/.local/share/mime/mime.cache r,
/home/*/.xchat2/ r,
owner /home/*/.xchat2/* rw,
owner /home/*/.xchat2/** rw,
owner /usr/bin/xchat mr,
/usr/include/python2.7/* r,
/usr/lib{,32,64}/** mr,
/usr/local/lib/python2.7/*/ r,
/usr/share/enchant/enchant.ordering r,
/usr/share/fonts/** r,
/usr/share/glib-2.0/schemas/gschemas.compiled r,
/usr/share/hunspell/ r,
/usr/share/hunspell/en_US.aff r,
/usr/share/hunspell/en_US.dic r,
/usr/share/icons/ r,
/usr/share/icons/** r,
/usr/share/mime/mime.cache r,
/usr/share/myspell/dicts/ r,
/usr/share/pixmaps/ r,
/usr/share/pyshared/* r,
/usr/share/tcltk/tcl8.5/init.tcl r,
/usr/share/themes/Ambiance/gtk-2.0/apps/* r,
/usr/share/themes/Ambiance/gtk-2.0/gtkrc r,
/usr/share/themes/Default/gtk-2.0-key/gtkrc r,
/usr/share/themes/Raleigh/gtk-2.0/gtkrc r,
/var/cache/fontconfig/* r,
/var/lib/dbus/machine-id r,

}

I can see a few areas that could be tighter, but I'm no longer on Ubuntu, so I can't do much to test it out.

---

### Post by Ms. Daisy on 2012-11-21
Open xchat, connect to whatever server you connected to before (freenode?). Click on "settings" and "preferences".  (see screenshot for details)

[ATTACH]227526[/ATTACH]

At the bottom of the list on the left you'll see "File Transfers"
See what the field "Auto Accept file offers" is set to: I would recommend setting it to "No" or "Browse for safe folder every time" 

If that was set to "yes" then you did indeed download an item.  Upload the mp3 file that you received to virus total to see if it's got any signatured malware in it.

---

### Post by Marbsie on 2012-11-22
My xchat was set to "Browse for safe folder every time" back when this first happened. I set it to no shortly after. I was never prompted to select a location for a download. If I had I as sure as hell would not have said yes :D

I have almost no mp3's at all so I did a quick search and found around 7 total. All dated to before this month so I now know I didn't accidentally download an mp3.

After a lot of searching I also found another forum where a guy asked how to block CTCP messages because they were annoying. My guess is he was dealing with the same thing. I believe it's called a "slot announcer" and I _think_ it's just an automatic "advertisement" for downloads.

Here is a screenshot that shows exactly what I saw. Since I don't know what the number strings are I censored them along with the usernames for their privacy. Told you I was paranoid :D

[ATTACH]227553[/ATTACH]

That was all moving by pretty fast.

I've uninstalled xchat. It's too much of a hassle for an Ubuntu noob like me.


Thank you both again very much for taking the time to help me out. I think my system is still secure (fingers crossed).

---

### Post by howefield on 2012-11-22
> **Marbsie said:**
> I believe it's called a "slot announcer" and I _think_ it's just an automatic "advertisement" for downloads.

Yep, that's what it is. An advertisment of the fact someone has download space(s) available.

---

