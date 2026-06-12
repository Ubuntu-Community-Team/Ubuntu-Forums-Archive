---
title: "Ubuntu one problem"
date: 2009-12-06
forum: Ubuntu One (CLOSED)
---

### Post by hgergo on 2009-12-06
Hello
I am usink ubuntu 10.04 and i have  the foloving problem wit ubuntu one

root@heavyd-laptop:/home/heavyd# u1sync --authorize
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 185, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 113, in wrapper
    return real_cb(real_s, condition)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 217, in callback
    self.simulate() # fire Twisted timers
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 729, in runUntilCurrent
    f(*a, **kw)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 73, in wrapper
    ent = func(*arg, **kwargs)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/u1sync/client.py", line 295, in _obtain_token
    oauth_client.clear_token()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 166, in clear_token
    items = self._get_keyring_items()
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 138, in _get_keyring_items
    self.consumer.key})
gnomekeyring.IOError: 



can sombody help?

---

### Post by duanedesign on 2010-01-28
I'm sorry to hear Ubuntu One isn't working properly for you. Can you try the following and let us know the results?

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. A web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

You should be connected after you follow these steps.

If you are not connected, you can file a bug by right-clicking the applet in the panel at the top of your screen and select 'report problem'.  Attach the following files to this bug report.

~/.cache/ubuntuone/log/oauth-login.log
~/.cache/ubuntuone/log/syncdaemon-exceptions.log

---

### Post by duanedesign on 2010-03-13
any update on whether or not this worked? I have come across another person with the same error in their logs and would like to know how to  help them :)

thank you,
duanedesign

---

### Post by ndefontenay on 2010-03-15
In the event that someone has lost his ubuntu one account information and is not able to retrieve his password (say the mail address is obsolete).

How can that person remove any trace of ubuntu one connection to this account? The idea being then to create a new account and add the computer.

---

### Post by joshuahoover on 2010-03-15
> **ndefontenay said:**
> In the event that someone has lost his ubuntu one account information and is not able to retrieve his password (say the mail address is obsolete).

How can that person remove any trace of ubuntu one connection to this account? The idea being then to create a new account and add the computer.

If you want to prep your machine for a new Ubuntu One account (moving from an old one), then you can follow this FAQ: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)

If you want to remove files and cancel an Ubuntu One account for an account you can longer retrieve your password for, I'm not sure there is anything you can do as we need a way to ensure you own the user, which is done through the email address.

Thank you,

Joshua

---

### Post by Mr.Kappa on 2010-05-28
I have a similar problem: my ubuntu one client cannot connect to the server (or at least that's what I think!). Once I enable my computer on the ubuntuone interface, the client remains like I haven't enable it :(

---

### Post by sgz on 2010-07-15
I, too, have a problem with Ubuntu One on lucid. It can't be added to the computer list: after I login into my Ubuntu One account via the mozilla window launched from the Ubuntu One settings dialog,  no "Add computer" button in the "https://one.ubuntu.com/account/machines/" page appears. I've got karmic at home, and there was no such problem (in fact, no problem at all) in the setup process there, though I created the account in lucid. Now, I've tried the FAQ solution for this
> Some users have reported problems with finding the  "Add Your Computer" button in this process. We believe this is due to  the Ubuntu One Preferences application (step 1) not launching your  default web browser (quickly enough... or at all) in order to proceed to  step 2. If performing step 1 does not open your web browser (or a new  tab if you already have a browser open) within a few seconds, please 

[LIST=1]
[*]close the  Ubuntu One Preferences application window (if it's already open)
[*]open your  Terminal (located in Applications >> Accessories)
[*]and type the following:
[/LIST]

 u1sdtool -q; killall ubuntuone-login; u1sdtool -cThis should force a web browser to open and put you at  step 2 of the process. This is temporary measure so users can get up and  running quickly. We will implement a more permanent fix for this  problem soon. and it doesn't work.

And the  (I guess  because the machine isn't added) the authorization fails with these:

> sgz@sgz-desktop:~$ u1sync --authorize
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 576, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 292, in got_state
    self.acquire_access_token(description, store)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 359, in acquire_access_token
    self.request_token = self.make_token_request(oauth_request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 247, in make_token_request
    self._forward_error_callback(e)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 160, in _forward_error_callback
    raise error
IOError: [Errno socket error] [Errno 8] _ssl.c:480: EOF occurred in violation of protocolAm I doing anything wrong? Thanx in advance :)

---

### Post by duanedesign on 2010-07-16
Can you check that Firefox is your default browser.

System --> Preferences --> Preferred Applications

Web Browser > Firefox

Additionally are you using a script blocking service like NoScript or are you behind a corporate or university proxy?

EDIT: looking at bug reports it does appear that the error you are getting is caused by a proxy. Ubuntu One does not yet support proxies. That is on the list of possible features in future releases.

[https://bugs.edge.launchpad.net/ubuntuone-client/+bug/387308](https://bugs.edge.launchpad.net/ubuntuone-client/+bug/387308)

---

### Post by sgz on 2010-07-16
So that's the blasted reason! I guess I should have studied the bug reports before asking. Thank you for the tip :) Firefox is my default browser, and I'm not using any script blocker, but I do use a proxy to access the internet at my workplace - no alternatives.

So, i guess we'll have to wait until it's fixed :(

---

### Post by Pifilatakanemu on 2010-07-17
There are still plenty of alternatives.

[Wuala]("http://www.wuala.com/referral/KC6FMCNNMBGNAJPKP4MC") and [Dropbox]("https://www.dropbox.com/referrals/NTIxNTQxNzg5") have good Ubuntu integration and work flawlessly.

Both are referral links of me. So if you register through the links, we both get 250mb in addition.

Once U1 leaves beta status and starts to work how it should you still can switch back. Or use Dropbox as a cross-platform alternative.

---

