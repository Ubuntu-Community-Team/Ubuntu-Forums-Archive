---
title: "Password protect Evolution"
date: 2009-05-29
forum: Security
---

### Post by mahasmb on 2009-05-29
I don't know if this is the right forum for this...

**I want to password protect Evolution, so that whenever someone opens it** (of course assuming it's not already running in the background)**  it would ask for a password, so that only I can use it**. Just like how Palm Desktop does on Windows as I use Evolution to sync my Palm Centro and have all my private stuff on it.

[SIZE="1"](Now this is my desktop computer in my room. I'm the one that uses it 95% of the time, but every now and then my parents or siblings jump on it for little things (checking e-mails, youtubing etc). My little brother can be quite nosy. There's no point in setting up a separate login account for this, and locking my screen or turning the computer off whenever I step away won't be fair if someone needs to use the computer in a quick rush. Plus, it'll be tedious for me as well.)[/SIZE]

I need this password to be different from my login password.

Any ideas? I can't find a thing that'll help either on Google or these forums. **Jpilot isn't an option, it messes up my Memos and Calendar. I'm fed up with it.**

---

### Post by Boondoklife on 2009-07-03
Really I can not see a good way to do this short of the second login. You might want to look into the auto login after time and setup a second account.

---

### Post by Luke22 on 2009-07-26
Have you found a solution to this yet?

**In theory, as a workaround, it should work to move the .evolution folder** (this is where Evolution saves all its data - it's a subfolder to your home folder, but I am sure you probably know this) **to an encrypted folder** (e.g. via encfs). You could then close evolution and stop the decryption of that folder. However, I tried it and got all kinds of read/write errors. I eventually had to delete the messed up .evolution folder and start afresh, so no luck there so far.

But I agree with you that this would be available as a simple password protection from within Evolution. Email is particularly sensitive for most people and I would love for this to be possible. And Outlook offers it, but then I don't want to use Outlook...

---

### Post by niteshifter on 2009-07-26
> **mahasmb said:**
> 
There's no point in setting up a separate login account for this, and locking my screen or turning the computer off whenever I step away won't be fair if someone needs to use the computer in a quick rush. Plus, it'll be tedious for me as well.)

Then what, pray tell is the point of having a multi-user OS under your fingers?

Create a "guest" account. Make it autologin. Restrict it as you see fit.
When you leave the machine switch users (via the GNOME fast user switch applet). Two clicks and you're out of your session, two clicks and type your password and you're back.

---

### Post by hggdh on 2009-07-28
There is no option to require Evolution to ask for a password for you to access it. There will be no such option: although I cannot speak for the developers/maintainers (and one of them might be crazy enough to think of this), this simply does not make sense -- and I would be one to fight against it, upstream (I am quite involved with Evo upstream).

Let's assume, for the sake of argument, that you indeed have a password on Evolution. So you have to *type* the password to get to Evolution. Now:

* what is the difference from typing a password for an encrypted ~/.Private directory?
* if the password is only for Evo, then I still can see all your emails, simply by looking at ~/.evolution

If you are sharing your *session* with other people, you have already given up on privacy. This is the, perhaps, the most important point... Privacy is a right that have to be exercised, or it will be lost.

Your options:

(1) use a web email, and remember to clean up the cache every time you leave the computer;
(2) use a *different* userid (as already proposed), and *encrypt* your Evo emails (create a ~/.Private directory, move ~/.evolution there, and create a sof link from ~/.evolution to ~/.Private/.evolution). Note that the ~/.gconf (and friends) will still be unencrypted, unless you encrypt your whole home dir.

Frankly, I do not see any other sensible option that is not a variant of these.

---

### Post by chainchomp on 2009-08-31
> **hggdh said:**
> 
* what is the difference from typing a password for an encrypted ~/.Private directory?
.
.
.
(2) use a *different* userid (as already proposed), and *encrypt* your Evo emails (create a ~/.Private directory, move ~/.evolution there, and create a sof link from ~/.evolution to ~/.Private/.evolution). Note that the ~/.gconf (and friends) will still be unencrypted, unless you encrypt your whole home dir.


The difference is that I would know how to type a password into Evolution if the option existed, but I don't know how to set up an encrypted ~/.Private directory with a sof link from ~/.evolution to ~/.Private/.evolution.

You say that sharing my session with other people means I have given up my privacy, but that's not exactly right. Because my parents/siblings would have no idea that ~/.evolution exists, or that they could also read my mail in ~/.evolution, and so, would not be able to read my mail. Yeah, I have given up my privacy if I share my session with a computer whiz, but not if I share it with an average person.  A password in Evolution would protect me from an average person.

---

### Post by hggdh on 2009-09-01
> **chainchomp said:**
> 
(...)
You say that sharing my session with other people means I have given up my privacy, but that's not exactly right. Because my parents/siblings would have no idea that ~/.evolution exists, or that they could also read my mail in ~/.evolution, and so, would not be able to read my mail. Yeah, I have given up my privacy if I share my session with a computer whiz, but not if I share it with an average person.  A password in Evolution would protect me from an average person.

We are talking about different paradigms. Ubuntu is a multi-user O.S. It is expected that every user will have their own userId, and will login/logout as needed. Evolution (and pretty much any other user application in *IX) runs under this paradigm.

To boot, trusting that other's ignorance will protect you (what is usually called "security by obscurity") has bitten back, every single time. People _start_ ignorant. They don't usually keep ignorant, at least not all of them.

As I said before, there is no such option. I would not expect we will have such an option any time soon, if ever. And I will still vote against it.

But you can propose it to the Evolution Maintainers, upstream. All you need is to email [email]evolution-list@gnome.org[/email].

---

### Post by ogromano on 2009-09-01
I am not saying I agree with either point in this post, but I do see the point with having a password... In many cases you will have to allow people to use your computer and whether it is something you planned ahead of time or not is the main difference. 

If you did plan ahead, then you probably installed everything to be accesible to other users, if not when someones wants to borrow your machine you have 2 choices, give them limited access with a new guest account that won't have that cool game or app or settings they saw you using or you let them use your session without logging out. 

In either situation, it is a case of how much you want to share your computer, which includes private stuff... I share my pics, my music, my games, the settings of my programs, etc, etc... and a password for certain things would be useful.  I am new to Linux and I don't know how to encrypt or make soft links and things yet... 

I guess the best solution for mahasmb would be to make normal accounts for each person that uses his comp... although it sounds like a hassle...

What do you think?

---

### Post by hggdh on 2009-09-01
> **ogromano said:**
>  

In either situation, it is a case of how much you want to share your computer, which includes private stuff... I share my pics, my music, my games, the settings of my programs, etc, etc... and a password for certain things would be useful.  I am new to Linux and I don't know how to encrypt or make soft links and things yet... 

I guess the best solution for mahasmb would be to make normal accounts for each person that uses his comp... although it sounds like a hassle...

What do you think?

There are many different ways something like this could be setup, although most of them will still be vulnerable to someone with knowledge of the system.

For the sake of argument, let's posit that:

1. the machine is left powered on, and logged in, without screen lock active;
2. Bob is the owner, Carol, Alice, and Tom are passers-by. Of course, the last three are the *expected* users -- since the machine is logged in, *anybody* could use it.

Now, Bob can wish to only block access to his email (say, via Evolution). But things will very fast get more complicated: Bob may now want to block Tom from Torrent, Alice and Tom from the web browser, and Carol from everything except OpenOffice.

And now what? Are we going to build yet another security interface for the same logged-in user? The O.S. already does that...

It would be much easier (but still worse than one account per user) to create two accounts: everybody (meaning Alice, Carol, and Tom, plus whoever else happens to have access to the machine), and Bob. Now Bob logs in and, using the Fast User Switch App, also logs in to the 'everybody' account. Whenever Bob leaves the machine, he first switches over to the 'everybody' account.

More work for Bob, of course. But now Bob guarantees nobody will be able to look at his Firefox settings, history, and (probable) saved password, nor use his Evolution accounts, etc, etc, etc.

One big no-no for shared accounts is the inability to audit who did what. Of course, this is not a worry here. Until it gets to be one, because -- say -- the BSA, or the RIAA, are knocking on the door with the police. Since Bob is the only known user, Bob gets the pleasure to be sued (and, incidentally, will also get parted from his computer for quite a while).

This idea, plainly put, is Not A Good Idea.

---

### Post by stccc on 2009-11-26
> **chainchomp said:**
> 
You say that sharing my session with other people means I have given up my privacy, but that's not exactly right. Because my parents/siblings would have no idea that ~/.evolution exists, or that they could also read my mail in ~/.evolution, and so, would not be able to read my mail. Yeah, I have given up my privacy if I share my session with a computer whiz, but not if I share it with an average person.  A password in Evolution would protect me from an average person.

What about this: Create a small program that asks for password. If the password is correct, the program then launches Evelution or whatever program you want to protect. You can then edit the evolution launcher in the application menu so that it points to this program.

---

### Post by cariboo on 2009-11-26
I wonder why so many people are against logging out or locking the screen when leaving the computer. hggdh suggestions is the most secure, just make sure you have permissions to your home directory set to 700, this will keep most average users from snooping through your email.

---

### Post by Chunky Dunk on 2009-11-27
> **niteshifter said:**
> Then what, pray tell is the point of having a multi-user OS under your fingers?

Create a "guest" account. Make it autologin. Restrict it as you see fit.
When you leave the machine switch users (via the GNOME fast user switch applet). Two clicks and you're out of your session, two clicks and type your password and you're back.

You could always be in a situation where you generally trust the person to be on your account, maybe for casually looking up something on the web, but you don't want them to have super easy access to emails you have stored on your computer. 

Personally I think it would be a nice optional feature to have.

---

### Post by Sprocketjoo on 2009-12-16
Bump!

I'm glad there are more people out there with the same request.

I always lock the session whenever I leave the computer at home. However, from time to time some friendly people (girlfriend, brother, etc.) will ask to check his/her webmail or surf the web a little bit. I know I could fast switch to some guest account, but they will probably wonder why can't they just access the browser already open by me... Even smart girlfriends could suspect and ask "why can't be share your session?". Moreover, if they see you opening Evolution and reading e-mail, they could easily plan to do it next time computer is unattended and get full access to mail history... A big temptation, for sure.

Actually the only problem in sharing a session with "friendly people" is JUST access to evolution. Everything else is protected or has no privacy requirements at all.

I guess Evolution could ask for an access password and store it in gnome-keyring just like it does for account passwords. Don't you think?

---

### Post by HermanAB on 2009-12-17
Hmm, a looong thread and nobody answered your question!

The solution to what you want to do lies with /etc/sudoers.  You need to edit that file and add an entry for Evolution such that the members of the 'users' group need to use a password to run the program.  Then create/edit the desktop and menu launcher to run Evolution using gksudo.

For some details, read 'man sudoers' and 'man gksudo'.

---

### Post by ClouDdM on 2010-05-26
Switch to Thunderbird. There you have a protection by being able to blank your mail until password is typed!

---

### Post by ClouDdM on 2010-05-27
Thunderbird also has a masterpassword the you have to enter before login in to the program

---

### Post by Sprocketjoo on 2010-05-27
Sorry I tried sudoers trick but it didn't work...

I understand some of you people switching to another mail client, this issue might be pretty important for some of us.

---

### Post by Boondoklife on 2010-05-27
Ya know I was just thinking, if people want their email to be under lock and key, what is the difference between this and just switching users?

In the password case, our friendly user will click on email and be prompted for a password. You can either "A" give it to them, assuming you trust them or "B" not give it to them and close it.

In the guest login case, our friendly user will click on email and see nothing but you will have to switch users.

It seems to me in either case, the suspicious party will want to know why they can not see your email, or even at best why you are looking over their shoulder while they do it.

---

### Post by Vikas Raidhan on 2010-05-31
This is a perfectly valid case. I don't want any guy to just open Evolution and read my messages. There is a reason why Lotus Notes, Outlook, etc have that extra layer of security. Email is considered to have highly sensitive and personal information at least more personal than data of other applications. 

So, instead of pondering over WHY can we just think on HOW.

BTW, I am also looking for such a solution. :P

---

### Post by OpSecShellshock on 2010-05-31
Not sure how you'd deal with existing messages, but you can always stop the sending and receiving of new messages by just not setting up the account to store the password. That would mean having to check manually for new messages, though. Other than that, forcing Evolution to have to run with elevated privileges would do that, but would be a horrible idea.

To be honest, anything that would do this would actually be more difficult, more tedious, and would take longer than just locking the screen or switching users. If you're going to have a shared computer, it just makes more sense to have an account for each user or use a guest account. If you just leave it open for others to use, then even if you could keep them from reading emails, they'd still be able to get at everything else in the home folder.

---

### Post by Boondoklife on 2010-05-31
> **Vikas Raidhan said:**
> This is a perfectly valid case. I don't want any guy to just open Evolution and read my messages. There is a reason why Lotus Notes, Outlook, etc have that extra layer of security. Email is considered to have highly sensitive and personal information at least more personal than data of other applications. 

So, instead of pondering over WHY can we just think on HOW.

BTW, I am also looking for such a solution. :P

For people with this type of case, I normally recommend some type of web-based mail. This will force the person to login to see email, assuming you have logged out of the page when you are done.

But for those that are hardcore and just want an option like this then why not just make a bash script with a zenity front end that asks for input, compare that to a known variable. If the input matches the variable then it opens, if not then it shows an error message. This would have the downfall of leaving the password visible to the user if they were to open the command in say gedit, but these are trusted users you are letting use your computer with your account logged in right? Really this is the only band-aid for your issue I can think of at the moment.

---

### Post by Sprocketjoo on 2010-06-09
> **OpSecShellshock said:**
> forcing Evolution to have to run with elevated privileges would do that, but would be a horrible idea.
Why?

> **OpSecShellshock said:**
> 
To be honest, anything that would do this would actually be more difficult, more tedious, and would take longer than just locking the screen or switching users. If you're going to have a shared computer, it just makes more sense to have an account for each user or use a guest account. If you just leave it open for others to use, then even if you could keep them from reading emails, they'd still be able to get at everything else in the home folder.

I disagree. I'm not going to have my computer shared, but eventually some guests would gently ask to use it. I don't care about my home folder, but I do care about people being able to read all of my e-mails.

---

### Post by Boondoklife on 2010-06-09
Why? Well let's see, if evolution is running with elevated privs that mean things it run will have those privs too. This is why Outlook tends to go ape when there is a malicious attachment. Just think if I sent you a script that had a simple rm -fR / and you clicked on it and ran it... The results would not be good either way but the whole system would suffer if it is ran as root vs. a user.

Hope that makes more sense.

---

### Post by pbenerjee on 2010-06-25
> **hggdh said:**
> There is no option to require Evolution to ask for a password for you to access it. There will be no such option: although I cannot speak for the developers/maintainers (and one of them might be crazy enough to think of this), this simply does not make sense -- and I would be one to fight against it, upstream (I am quite involved with Evo upstream).

Let's assume, for the sake of argument, that you indeed have a password on Evolution. So you have to *type* the password to get to Evolution. Now:

* what is the difference from typing a password for an encrypted ~/.Private directory?
* if the password is only for Evo, then I still can see all your emails, simply by looking at ~/.evolution

If you are sharing your *session* with other people, you have already given up on privacy. This is the, perhaps, the most important point... Privacy is a right that have to be exercised, or it will be lost.

Your options:

(1) use a web email, and remember to clean up the cache every time you leave the computer;
(2) use a *different* userid (as already proposed), and *encrypt* your Evo emails (create a ~/.Private directory, move ~/.evolution there, and create a sof link from ~/.evolution to ~/.Private/.evolution). Note that the ~/.gconf (and friends) will still be unencrypted, unless you encrypt your whole home dir.

Frankly, I do not see any other sensible option that is not a variant of these.


How can we call an Evo developer crazy if she thinks a password requirement is genuine?? This is autocratic windows syndrome from this Linux learned poster
If he has an ear of Evolution team then I feel sorry about average Evo user, myself included.

If so many people feel embarrased locking/logging out their machines to trusted family/friends, why are we imposing our opinion on them? Email is EXCEPTIONAL application when it comes to privacy to average Joe. I understand the philosophy of multi user OS but its always nice (or required for some people) to have an OPTIONAL password feature in your email application.

Digressing a little, I love evolution but hate the fact that it takes its online/offline internet status from network manager (which in turn, doesn't handle USB broadband modem connection; I use GNOME-PPP). That means, though I am actually connected to internet, evolution takes network manager's word that I am offline and starts in offline status everytime.

Firefox too, had the same issue and its steering team, being sensitive to user community, provided a workaround within application instead of playing ping-pong with network manager developers. How difficult is it for Evolution team to give an option to disable/enable the network manager feedback (and start with online status by default) ??

Coming back to the thread's topic, is expecting the same sensitivity from Evolution team too much to ask for?? The same autocratic handling is showing up in the problem/need raised in this thread too.

I suspect this inflexible attitude is forcing thousands of Evolution users to the ugly Thunderbird

All they need to do is agree to provide an additional password for super sensitive email application and not throw the multi user OS philosophy at average Joe. Email is exceptionally private and let's give the user a choice whether she wants to type a password at Evo start up or after logging back to system again??

---

### Post by rookcifer on 2010-06-25
nevermind.

---

