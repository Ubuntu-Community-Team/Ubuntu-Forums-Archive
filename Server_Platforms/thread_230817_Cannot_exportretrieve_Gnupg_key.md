---
title: "Cannot export/retrieve Gnupg key"
date: 2006-08-06
forum: Server Platforms
---

### Post by stanz on 2006-08-06
Hi All,
Sorry for the double thread, but, I totally put this out of reach..:
[http://www.ubuntuforums.org/showthread.php?t=229836](http://www.ubuntuforums.org/showthread.php?t=229836)
==========
I've been searching for days & I'm bleary eyed...:sad:
I recently loaded gnupg with the assistant & managed to do the
clearsign for the CoC.
Needing to sign guidelines for the new users network, I came to find 
I'm unable to export my key.
using the cli, output is:** *nothing exported***.
using assistant, gives **i*nternal error*** - choosing diff servers - nothing happens.
I've been trying to adjust conf files - with no change...as a newbie!
I've tried the web interface, at one keyserver site, which said it uploaded
a key - once - but when I tried to search, to verify I did it right
It had no key on server.  ](*,)    I found I Do, have it on BigLumber.com, but-
can't get it!
Now..I Have a FRESH INSTALL, of Dapper... and want to use that same key!?
Possible ??
I've found repeated instructions, on how to- but no trouble shooting info.
Anyone with same problem & fix ?
Thanks in advance......

_Moderator: Please Delete Other Post.... please ?_

---

### Post by mlind on 2006-08-07
Have tried following [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto) ?

---

### Post by stanz on 2006-08-08
> **mlind said:**
> Have tried following [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto) ?
Yep, I did...It has No Trouble Shooting Help...
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto) ...nor does:
[http://www.gnupg.org/gph/en/manual.html](http://www.gnupg.org/gph/en/manual.html)
[http://www.gnupg.org/(en)/documentation/faqs.html#q5.8]("http://www.gnupg.org/%28en%29/documentation/faqs.html#q5.8") :  Last-Modified: Jul 30, 2003 
[http://www.gentoo.org/doc/en/gnupg-user.xml#doc_chap4](http://www.gentoo.org/doc/en/gnupg-user.xml#doc_chap4) : not bad
[https://help.ubuntu.com/community/UnsignedGpgKey](https://help.ubuntu.com/community/UnsignedGpgKey) : result of search
[https://help.ubuntu.com/community/GPGsigningforSSHHowTo](https://help.ubuntu.com/community/GPGsigningforSSHHowTo) .

It's all good info, for starting to make key & use it...as long as you know what & how to use commad line interface !

I made my key, on Breezy - with gnupg gui, with no permission hassles.
Now on Dapper, coming preinstalled & set - Seahorse wouldn't do things - untill I figured out to : sudo seahorse !!
But I still can't import My key from file - into gui window.

I wanted to try learn & figure this out, before revolking this key & just start fresh by making another....
And then sign things ALL over again.....:-({|=

Thx for your reply mlind....

---

### Post by mlind on 2006-08-08
Are you trying to send your public key to gpg keyserver or export it as a file?

---

### Post by Ride Jib on 2006-08-08
> **stanz said:**
> ....
Now on Dapper, coming preinstalled & set - Seahorse wouldn't do things - untill I figured out to : sudo seahorse !!...

Not questioning you as I haven't tried it myself, but this seems wrong. What if a non-sudoer user wanted to secure their stuff as well? Are they not able to use Seahorse?

---

### Post by stanz on 2006-08-09
> **mlind]     Are you trying to send your public key to gpg keyserver or export it as a file?[/quote]I was trying to do Both. 
Because, from signing the CoC, My key needed to be sent [exported] to launchpad, -that worked, - on dapper UPgrade w/gnupg.
After Fresh Install, Having copied & saved my keys elsewhere, I needed them back & in this box[pc].
I'm expecting to see them appear in the gnupg gui, as before- but nadda.
I cannot send or retrive keys - by way of gui's server, response- "internal error", which to me- has shown NO interaction on my DSL modem.
After uninstalling gnupg, and installing seahorse [which btw maybe I shouldn't have chose the "set uid [?] to root" ?] - clicking on a 'key' file- in .gnupg folder - changes it to a ".gpg" file. I thought It was all getting better...
But it won't appear as one of MY keys- in the gui - EVEN with 'sudo'.

Signing mail with Evolution was good- until this change also. So it ain't working there either.
I've used the 8 diget # as key ID, tried the fingerprint...nadda.
This creat messege...??...All I did was choose to sign.
> **Could not create message.**
Because "gpg: /home/stanz/.gnupg/gpg.conf:32: argument not expected ", you may need to select different mail options. > Line 32:: # added from: [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
#32/ export GPGKEY=B6C86915 So..no signing or encrypting...

[quote=Ride Jib said:**
> Not questioning you as I haven't tried it myself, but this seems wrong. What if a non-sudoer user wanted to secure their stuff as well? Are they not able to use Seahorse?
I'm wondering if "I Didn't Work This RIGHT", for gnupg or seahorse.
So I may need to revoke key & start from beginning?
Does anyone know about that config choice - with seahorse install -
about root-suid or uid?  Might that be my trouble?

---

### Post by LordHunter317 on 2006-08-10
POst the command and the line, unaltered.  Your line is clearly 
bungled, but I can't tell what you have in there.

This is rule one of technical support.  No one here has followed it, for shame.

---

### Post by stanz on 2006-08-10
> **LordHunter317 said:**
> POst the command and the line, unaltered.  Your line is clearly bungled, but I can't tell what you have in there. This is rule one of technical support.  No one here has followed it, for shame.
Hi LordHunter317,  Thanks for your response...
I Think your asking about this: 
[U]"**Could not create message. **Because "gpg: /home/stanz/.gnupg/gpg.conf:32: argument not expected ", 
you may need to select different mail options.
[/U]Which isn't from command line - it's from the gui, using evolution.
In the 'security' tab, by checking 'PGP Sign', when replying mail.
I'm not very commandline able, at this point - so much of this is gui.

I showed line # 32, of the : /home/stanz/.gnupg/gpg.conf:32 file, being what was added from advice at: [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
which is: 'export GPGKEY=B6C86915'.
I also have "use-agent" uncommented.

I hope this answers your question. Thx

---

### Post by stanz on 2006-08-10
I thought to grab Thunderbird, from the repos and try it...I've used it in the past & liked it.
So...I continue setting it up & move into Security & OpenPGP with Enigmail stuff, and it sets itself up from my choices, and then sez it's got my key & shows me MY default key..as:
**" 0x**B6C86915 ", the bold 0x being a new addition and new to me.
So...I cruize into evolution & change my key ID to that.
I recieved NO errors replying to a mail. :confused:
I did not use that - with 1st set-up, when it worked.
Seems something has changed? And I'm still clueless as to what or how.
I'll try en/decrypt as soon as I get more time...I just wanted to let ya all know of this...Thx ..

---

### Post by stanz on 2006-08-11
Well - Thunderbird is working fine...
I can sign & en/decrypt, & I got the plugin working in gedit.

Calling seahorse with: [I]sudo seahorse
[/I]NOW shows My Key & one recieved from Automatix install.

Sending a Signed messege with Evolution seems to be working,
BUT - when I want to send a: signed & encrypted messege, I get a window:
> **Could not create message.**
Because "Failed to execute gpg: Broken pipe", you may need to select different mail options. No help at all, to help me understand whats wrong or how to fix!
Well, if no one has been thru this, I'll dump evolution. :mrgreen:

---

### Post by stanz on 2006-08-11
Well...since I figure - I'm posting to myself...I mailed & directed attention to this thread, to: [gnupg.org]("http://www.gnupg.org/%28en%29/index.html") & their: [Howto's.]("http://www.gnupg.org/%28en%29/documentation/howtos.html") 
After another problem with: line 33 = export GPGKEY=0xB6C86915, I commented it out [#].
Then trying to reply - with sign/encrypt, my new error window says:
> Could not create message.
Because "can't connect to `/tmp/gpg-5Ydosq/S.gpg-agent': No such file or directory
gpg: can't connect to `/tmp/gpg-5Ydosq/S.gpg-agent': connect failed
gpg: writing to `-'
gpg: DSA/SHA1 signature from: "B6C86915 stanz <my@addy>"
", you may need to select different mail options. I've been selecting different mail options all week!!! [I notice the lacking of the **0x** from above!]
S.gpg-agent - what is this now?

Seeking to use the agent, I TRIED to follow advice from here:
[Configuring GnuPG to use a GPG Agent]("http://www.gentoo.org/doc/en/gnupg-user.xml#doc_chap4") ,which is direct for KDE users, But - unclear to this newbie using Gnome.
I think it gave me another folder, besides the one to create:
*/home/stanz/.gnupg/gpg-agent-i_nfo-stanz_*  ???
So, I have no clue about either one, or configuring them!

Thunderbird still works fine...I think?  ;)

---

### Post by starNIX on 2006-09-05
Same problem here.  Any solutions yet?

---

### Post by stanz on 2006-09-05
> **starNIX said:**
> Same problem here.  Any solutions yet?
I couldn't figure it out myself and also-I've been to busy at school-to continue.
I worked around it by using Mozillas' Thunderbird-which worked without a hitch.
BUT...and this is a biggie...I had to do a fresh install this week.
I didn't load the "*gnupg-agent" *-but I grabbed Seahorse again--but *Un-ticked*-
the option, to have it run "*suid*."
I saved my key elsewhere-grabbed it back-and was able to import it, using seahore, and its key agent.
I also just got to the point of signing a mail-using Evolution with success!   :mrgreen:

If you got Seahorse and opted to the "*suid*" thing, I remember it saying that-it can be changed by: *dpkg -reconfigure seahorse*

I don't know if that was the problem-to begin with, but so far-It's working ok.

Hope this helps!     ;)

---

