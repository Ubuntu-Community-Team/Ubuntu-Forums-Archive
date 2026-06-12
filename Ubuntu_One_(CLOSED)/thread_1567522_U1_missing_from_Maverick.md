---
title: "U1 missing from Maverick?"
date: 2010-09-03
forum: Ubuntu One (CLOSED)
---

### Post by locosway on 2010-09-03
After installing 10.10 I was asked to do a partial upgrade. During this upgrade several packages relating to the U1 service were removed.

I now do not have the U1 client, nor the Music Store service in Rhythmbox.

---

### Post by locosway on 2010-09-03
Looks like this is the problem...

The following packages have unmet dependencies:
 ubuntuone-client-gnome : Depends: ubuntuone-client (= 1.3.92-0ubuntu2) but 1.3.99-0ubuntu1 is to be installed
E: Broken packages

Instead of requiring anything equal to or greater than the version, it's locked into 1.3.92 which isn't in Ubuntu 10.10.

---

### Post by gr3gg0r on 2010-09-04
Any word on the status of this?  So far I haven't been able to get U1 to completely install because of this.

---

### Post by locosway on 2010-09-04
> **gr3gg0r said:**
> Any word on the status of this?  So far I haven't been able to get U1 to completely install because of this.

I think they have just over 30 days before release, so sometime before then I'd imagine it would be fixed.

That is of course if someone is aware of the issue, not sure if there's a bug filed.

---

### Post by gr3gg0r on 2010-09-04
I also just came across this: [http://packages.ubuntu.com/search?suite=maverick&keywords=ubuntuone-client-gnome](http://packages.ubuntu.com/search?suite=maverick&keywords=ubuntuone-client-gnome)

According to that, I think the problem is that ubuntuone-client-gnome is stuck in 1.3.92 for amd64 but there is the *correct* version (1.3.99) for i386.

So ... we need an amd64 version 1.3.99 ... Once we get that, I think we'll be good.

Maybe I should try to find/submit a bug report on this ...

---

### Post by altor on 2010-09-04
This works on 10.04:
[http://ubuntuforums.org/showthread.php?t=1531179&highlight=me+menu](http://ubuntuforums.org/showthread.php?t=1531179&highlight=me+menu)
(post #5)
No way on 10.10
Bye

---

### Post by locosway on 2010-09-04
> **altor said:**
> This works on 10.04:
[http://ubuntuforums.org/showthread.php?t=1531179&highlight=me+menu](http://ubuntuforums.org/showthread.php?t=1531179&highlight=me+menu)
(post #5)
No way on 10.10
Bye

That's not relevant to this thread, it's a different issue all together.

---

### Post by gr3gg0r on 2010-09-04
Looks like on my latest sudo apt-get update, the issues are resolved.

---

### Post by locosway on 2010-09-04
Yep, resolved now.

---

### Post by locosway on 2010-09-04
> **locosway said:**
> Yep, resolved now.

Actually, I spoke too soon...


```
greg@moniker:~$ ubuntuone-preferences 
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/bin/ubuntuone-preferences", line 1036, in got_newcredentials
    self.present()
  File "/usr/bin/ubuntuone-preferences", line 1016, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 692, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 167, in __init__
    raise ValueError("No pairing record for ubuntuone.")
ValueError: No pairing record for ubuntuone.
```

Here's the actual bug report..

[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/625767](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/625767)

---

### Post by afrowildo on 2010-09-06
The Ubuntu One packages were disable for me during my initial upgrade to 10.10. Now after having performed the partial upgrade today, I've regained access to the music store, though I don't appear able to sync anything yet. I'm guessing that since it's still beta software, we're going to be seeing this sort of thing over the next month.

---

### Post by duanedesign on 2010-09-08
Their was a bug in the ubuntu-sso-client that was preventing folks running Maverick from authenticating. The fix is going to be uploaded later today or tomorrow. If by the end of the week you are still not able to connect please post that here and I will try and help.

In Maverick Ubuntu One currently is not available under the Me Menu as it was in Lucid. You can still find it under System > Preferences > Ubuntu One. I will try and find out if this second issue is a permanent change or a bug.

thank you,
duanedesign

---

### Post by duanedesign on 2010-09-09
looks like the new ubuntu-sso-client package has been uploaded. After running the updates Maverick U1 should be syncing again.

---

### Post by altor on 2010-09-10
Upgraded, but no joy.
No way to reach the "add computer page" neither from the gui nor from command lines...
Bye!

---

### Post by duanedesign on 2010-09-11
Sorry the update made it to the [nightlies PPA]("https://launchpad.net/~ubuntuone/+archive/nightlies"). You can add it with the command.

```
sudo add-apt-repository ppa:ubuntuone/nightlies
```

then run

```
sudo apt-get update; sudo apt-get upgrade
```

If you don't want to add the Nightlies PPA the update should make it to the regular repository on around Tuesday.

---

### Post by altor on 2010-09-11
Something works!
Now I see the new computer on my account. 
It was added without seeing the "add computer" page. (As a matter of fact before I realised that I added three/four new computers...).
But in the gui I still see "local machine" instead of the name of the new one and unknow instead of my name/email...

---

### Post by duanedesign on 2010-09-11
@altor,
can you check a line in the following file.

run the command:

gksudo gedit /usr/lib/pymodules/python2.6/ubuntu_sso/main.py

and look for the line (near the top):

> PING_URL = "http://edge.one.ubuntu.com/oauth/sso-finished-so-get-tokens/"

It needs to be **https**, not **http**. So it will be:

> PING_URL = "https://edge.one.ubuntu.com/oauth/sso-finished-so-get-tokens/"

Note: If you have the version from the nightlies PPA this should already be done.

Then restart the Ubuntu One processes:

```
killall ubuntu-sso-login; u1sdtool -q;u1sdtool -c
```

---

### Post by altor on 2010-09-11
@duanedesign

1. The change is OK, I read:
PING_URL = "https://edge.one.ubuntu.com/oauth/sso-finished-so-get-tokens/

2. Here is the ouput of the commands you suggested:
alberto@alberto-laptop:~$ killall ubuntu-sso-login
alberto@alberto-laptop:~$ u1sdtool -q
ubuntuone-syncdaemon stopped.
alberto@alberto-laptop:~$ u1sdtool -c
alberto@alberto-laptop:~$ 

nothing else, no errors, no web page.

3. If I sign in in Ubuntuone I see the computer I was able to add to my account as I said in my previous message. Furthermore, now (for the first time) I can mark folders to syc, and they are uploaded/syncronised on my UbuntuOne account.


4. The only thing is that I miss is the proper setting of the U1 Gui, but really I don't think that it is important for me. But I undersatand that it should be fixet too.....

I hope that it can help..

---

### Post by duanedesign on 2010-09-13
@altor,
So on the Ubuntu One Preferences 'Devices' Tab you do not see your computer listed, only <Local Machine>? You are able to sync items however?

Could you run the following in a Terminal. This will open the U1 Preferences from the command line and might print some clues as to what is happening.

```
ubuntuone-preferences
```

thank you,
duanedesign

---

### Post by altor on 2010-09-14
> **duanedesign said:**
> @altor,
So on the Ubuntu One Preferences 'Devices' Tab you do not see your computer listed, only <Local Machine>? You are able to sync items however?

Yes I am able to sync items however! :D

When I run
```
ubuntuone-preferences
```

I see the GUI with only <local machine> and I get:

```
 :~$ ubuntuone-preferences
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/bin/ubuntuone-preferences", line 1036, in got_newcredentials
    self.present()
  File "/usr/bin/ubuntuone-preferences", line 1016, in present
    self.dialog.connect_desktopcouch_exclusion()
  File "/usr/bin/ubuntuone-preferences", line 692, in connect_desktopcouch_exclusion
    self.dcouch = dcouch.ReplicationExclusion()
  File "/usr/lib/python2.6/dist-packages/desktopcouch/replication_services/ubuntuone.py", line 167, in __init__
    raise ValueError("No pairing record for ubuntuone.")
ValueError: No pairing record for ubuntuone.

```

Tell me if I can give further help!

Bye

---

### Post by gr3gg0r on 2010-09-15
I'm also still not able to get ubuntu one working in maverick.  Any progress?  I'm getting basically the same stack trace as others when I run ubuntuone-preferences, however, I am *not* able to sync any files.

Anytime after I restart and attempt to connect with u1sdtool, I'll check the status and it says "Auth Failed".  Even though when I click the Manage account link in the preferences, it will take me to one.ubuntu.com and have me logged in without any interaction on my part.

---

### Post by duanedesign on 2010-09-16
The updates have made it to the Maverick repository (not just the nightlies). If you are still unable to connect and getting the AUTH_FAILED it is likely that you have a broken Token in the keyring that was created with the broken client. make sure your Maverick is up to date and then delete the U1 token and reauthorize.
NOTE: Their was a user that came into #ubuntuone today who had multiple tokens to delete. They were "UbuntuOne token for https://ubuntuone.com" and "Ubuntu One"


1. Close the Ubuntu One Preferences and open a Terminal (Applications -> Accessories -> Terminal)and run the command:

```
killall ubuntu-sso-login
```

2. Open Seahorse (System -> Preferences -> Password and Encryption keys) and delete the Ubuntu One Token.

3. Then open Ubuntu One Preferences (System -> Preferences -> Ubuntu One). You should be prompted to add your computer. this new token should work.

thank you,
duanedesign

---

### Post by altor on 2010-09-16
1. I have updated (but without cancelling the nightlies repository).

2. I have followed the duane's instruction

3. No screen to add a new computer. Anyway, after some time I have seen that there were added "new computers" (4 or 5) but I wasn't able to syncr. any more.

4. I cancelled all such computers and I used the command lines duane's suggested above. After some time I sow again some "new computers".

5. I cancelled all of them except one and now I am able to syncr again

6. Anyway the GUI always shows  <local machine>.

As a matter of fact, I am able to add the new computer (better "some computers" :) ) without  the add computer page.  When I cancel the Ubuntu One token I can't as well reach the add computer page (but it only asks me the pwd to connect or to buid a new account).

In my opinion there is something "strange" in my PC configuration tha con't be fixed.
 Anyway, I am quite happy how Ubuntu One actually works on my machine!!! :D :D

Bye!

---

### Post by altor on 2010-09-22
I see some upgrade coming from nightlies repository:
is it safe to upgrade or is it better to wait for "standard" repository and, eventually, cancel nighlies...

Bye

---

