---
title: "Controlling files listed by directory request"
date: 2011-05-05
forum: Server Platforms
---

### Post by SacramentoRob on 2011-05-05
hi Folks, 

I use Apache 2.0.55 (Ubuntu) as a document server for a business association.  When the document files expire, I change the permissions so that only the owner can open them but I like to leave them on the server so that they are all in one place.

Here is my trouble--when visitors come to the site and get the directory listing, all the document files show up, whether the visitor can access them or not.

Is there some way to configure the server to not show the inaccessible files?

I guess a few technical details might help.  During their useful lives, the files permissions are set to 644.  Once they expire, I change them to 600.  After the change, the files are still visible.  Setting them to 000 doesn't help either.

It might be of note, but directories behave differently than files.  If I set a directory to 600, it disappears from the listing.

I'd appreciate any advice you might have, 

Thanks, 

/Rob

---

### Post by dtfinch on 2011-05-05
If this were a Samba server, there'd be a "hide unreadable" option you could use.

Are you asking about Apache's built-in directory listings, or are you using webdav, or do you have a website (like php) running on top of Apache serving them?

I'm not aware of much for Apache's built-in listings. You could probably jury-rig something together with mod_autoindex's DirectoryIndex option and scheduled scripts, but I don't think it's something Apache's meant for, and it's not something I've used.

---

### Post by SacramentoRob on 2011-05-24
Hey DT, 

Thanks for getting back to me on this.

As you guessed, yes, I am using the default Apache directory listing.

I tried fiddling with the DirectoryIndex but I couldn't figure it out.  

I'll head off to try to figure this out with Samba.

thanks again, 

/Rob

---

