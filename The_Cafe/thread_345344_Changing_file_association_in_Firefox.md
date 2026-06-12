---
title: "Changing file association in Firefox?"
date: 2007-01-24
forum: The Cafe
---

### Post by finferflu on 2007-01-24
Hi, I'm posting here because this is not an Ubuntu related question.

In the past I've been so happy with KDE that I set Amarok as my default player for almost anything, including Firefox. Whenever I want to play a stream, an m3u file, I set it to open it with Amarok. That was fine until I've moved to E17, now I would like to have Exaile as my default player for m3u files, but I don't know how to change this.
I think there should be some kind of option within Firefox (2.0), since I've set that file association with it, but I can't find. I went to Edit > Preferences > Content > File Types, but in the list I can only find two file formats, MP3 and SPL, and nothing more...

What am I missing?

Thanks a lot!

---

### Post by MkfIbK7a on 2007-01-24
try right clicking on the link

"Save as"

it should say
 
open or save

and also something like
 
opens with amarok

i think you can change it there

hope this helps:D

---

### Post by finferflu on 2007-01-24
Too bad, when I select "Save Link As.." the file shows as a .html format, whereas when I copy the link location, I can play it, for example in VLC... weird...

---

### Post by Mateo on 2007-01-24
Firefox really needs to make things like that easier.  I think if you go to Options > Content and then at the bottom it says file types, might be able to change there (there might be a config file too).

I wish firefox would set different download locations for different file types.  There are certain file types that I know I always want saved in a specific folder, and most everything else I'd rather just save to the desktop.

---

### Post by mips on 2007-01-24
Havent used e17 but can you not right click on a local m3u file, selct properties and do the association over there ?

---

### Post by finferflu on 2007-01-24
In my first message I have said I've done that already, but no m3u file type appears in the list...

There is an add-on for the option you want, it's called Download Sort. ;)

---

### Post by finferflu on 2007-01-24
Ok, I've found a link to a .m3u file, and it wasn't associated with anything, and I've associated it with exaile, and when I set it as default there was written that I could change it again in the Content menu. I went there, manage file association, and there was no .m3u file extension in the list. Moreover, I've found out that the extension I wanted to change was not .m3u. I don't know how to find out what format it is. 
Could somebody go to [www.jamendo.com](www.jamendo.com), hover on an album and click on "Listen" to tell me which format it is?

Thanks a lot!

---

### Post by mips on 2007-01-24
> **finferflu said:**
> 
Could somebody go to [www.jamendo.com]("http://www.jamendo.com"), hover on an album and click on "Listen" to tell me which format it is?


It's .m3u

Edit:

If you hover over an ablbem and slect listen it downloads a files called jamendo-playlist.m3u which does not get played automatically on my system with real player.

If however you click on the album and then click on the little speaker next to a track name it will automatically open in realplayer for me.

---

### Post by finferflu on 2007-01-24
> **mips said:**
> It's .m3u

Edit:

If you hover over an ablbem and slect listen it downloads a files called jamendo-playlist.m3u which does not get played automatically on my system with real player.

If however you click on the album and then click on the little speaker next to a track name it will automatically open in realplayer for me.

That's very weird. I had the Mplayer plugin installed, and it used to play in an embedded Mplayer window, which I hated, since it didn't show the playlist... I'm really getting lost, and maybe giving up...

---

### Post by mips on 2007-01-24
Ok, I don't think real player actually likes the playlist that much, maybe it needs a plugin or something.. I changed the association in Firefox to Open with 'Amarok' and it works just great with Amarok. Amarok is the dogs bollocks :)

Thanks for the link to the site though, some nice music on there. listenig to Ehma & Rob Costlow right now.

---

### Post by finferflu on 2007-01-24
I know Amarok is amazing, the only problem is that it's a spaceship, it takes a lot to startup, especially when it's not on KDE. I prefer it over all the media players, though, that's why I think I'l just cope with the slowness...

As for Jamendo, this is [my profile]("http://www.jamendo.com/en/user/finferflu/albums/"), with the albums I like, you may like to dig in it, especially if you like ambient, electronica, instrumental, soundtrack, and so on...

---

### Post by Mateo on 2007-01-24
> **finferflu said:**
> 
There is an add-on for the option you want, it's called Download Sort. ;)

well, I already have enough add-ons as it is.  not sure if I want another one hogging up memory for something i don't use all the time anyways.  do you think if I installed it, set the associations, and then uninstalled it they would stick?  might try that.

---

### Post by finferflu on 2007-01-24
> **Mateo said:**
> well, I already have enough add-ons as it is.  not sure if I want another one hogging up memory for something i don't use all the time anyways.  do you think if I installed it, set the associations, and then uninstalled it they would stick?  might try that.

I don't think it would work anymore once uninstalled, but you might give it a try, and let me know if it worked ;)

---

### Post by bionnaki on 2007-01-24
this is what you do:

in the address bar, type about:config
then type browser.download.hide_plugins_without_extensions
double-click on the value and change it to "false"

go to firefox perferences and change the behavior as you want.

---

### Post by banjobacon on 2007-01-24
> **finferflu said:**
> That's very weird. I had the Mplayer plugin installed, and it used to play in an embedded Mplayer window, which I hated, since it didn't show the playlist... I'm really getting lost, and maybe giving up...

So, you've uninstalled the mplayer plugin?

When I click on Listen in Jamendo, I get a dialog box asking whether I want to open the file with Totem or save it to disk. It also has a checkbox that says "Do this automatically for files like this from now on." I'm guessing you selected this option once upon a time, and now are regretting it.

I don't know how to disable that option, though.

---

### Post by bionnaki on 2007-01-24
no need to.
just change the value to to false
and then go into preferences & manually change your settings.

---

### Post by Mateo on 2007-01-24
I don't see how that would work bionnaki.  he wants to change the default application for m3u files.  Doing what you do unhides plugins without an extension.  m3u doesn't show up that way.

---

### Post by finferflu on 2007-01-24
> **bionnaki said:**
> this is what you do:

in the address bar, type about:config
then type browser.download.hide_plugins_without_extensions
double-click on the value and change it to "false"

go to firefox perferences and change the behavior as you want.

Thanks for your help! Your suggestion worked! Thank you very much! :D 

> **banjobacon said:**
> So, you've uninstalled the mplayer plugin?

When I click on Listen in Jamendo, I get a dialog box asking whether I want to open the file with Totem or save it to disk. It also has a checkbox that says "Do this automatically for files like this from now on." I'm guessing you selected this option once upon a time, and now are regretting it.

I don't know how to disable that option, though.

That's exactly what happened, I haven't uninstalled the Mplayer plugin though. 

> **Mateo said:**
> I don't see how that would work bionnaki.  he wants to change the default application for m3u files.  Doing what you do unhides plugins without an extension.  m3u doesn't show up that way.

I could recognize the file format I was looking for by looking the application associated with it, that is, AmaroK. The file format was XSPF. 

Thank you everybody for your time and your help! :KS

---

