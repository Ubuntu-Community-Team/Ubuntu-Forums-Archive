---
title: "Best app for my needs?"
date: 2011-05-24
forum: Server Platforms
---

### Post by ClientAlive on 2011-05-24
Hi,

I'm running Ubuntu 10.04.

Part of my job requires transferring data to some of the people I work with. Until now I had been using email and sending attachments; but, with our newest project, it seems that what I need to send is often too large to send in one email.

I use a laptop computer that is about 5 or so years old. It is an HP Pavilion ze2000 with 1 gig of RAM; and, I think, 1.4 or 1.8 ghz processor (an AMD Turion 64).

Currently I am working with a web designer and will need to provide many large images in the coming couple weeks. I've gotten to thinking it would be convenient if I could install some software on this machine that would allow him to sftp a folder from my machine. The problem is I have never done anything like this before and it would have to be easy enough for a first timer to set up and get working properly.

Some of the criteria for the software would be:

* Free
* Simple
* Secure (not like plain ftp which can be sniffed seen by anyone looking)
* Standard (in the sense that most people will have what's needed to use the protocol - for example: zip compression is very standard. Most people use Windows, some Mac, and some Linux but all have zip)
* Ability to create more than one account for different people/ content (lets say I want to share 'this' with Joe and 'that' with Paul but I don't want either of them to see or access the other's stuff)
* Ample documentation that is easy to understand and learn from (some of the documentation one sees seems to reveal some kind of strange, acronym fetish on the part of the author)
* Preferably available in a repository where it can be installed easily through the terminal


What is the best program for me?? Does anyone have a suggestion??

Thanks in advance for the help. I'm hoping to implement something as quickly as possible since this project is already underway and we have need of something like this quickly. I hope I get some responses soon.

Thanks

---

### Post by ClientAlive on 2011-05-24
What about Bazaar?

[http://en.wikipedia.org/wiki/Bazaar_(software](http://en.wikipedia.org/wiki/Bazaar_(software))

But I wonder if it is accessible to those using windows or mac?


Or what about Python Paramiko?

[http://www.lag.net/paramiko/](http://www.lag.net/paramiko/)

But it says it is a - module? And I'm not sure it is server or client?

---

### Post by arrrghhh on 2011-05-24
Why don't you use SFTP...?  Seems like the simplest solution to me.  It's secure, free, standard...

---

### Post by ClientAlive on 2011-05-24
Secure ftp (or sftp) is a protocol isn't it? Or are you naming and application?

I don't know enough about any of it to know whether I already have the app/ apps I need by default with my Ubuntu installation or if I need to install something. If I need to install something I don't know what is the best to use for a newb and that does the things I need it to. The challenge is that I need to implement something very soon. I'm reading everything I can find but I can only read and absorb the information so fast. I was hoping someone would name an app or point me in the right direction so I can at least get to focusing on the right thing and hopefully get something implemented in the next couple days.

So far I've looked into:

* Ubuntu One - This is not what I described but I would have settled on it if it did what I need it to. I can not ask/ require those I work with to sign up for an Ubuntu One account in order to use the service. Unfortunately Ubuntu One is not an option for me at this time.

* openSSH - looks like it is very standard but I'm a little concerned about two things. (1) whether I will have the technical ability to set it up and use it, and (2) whether non-Linux users will be able to access it.

It's just that I didn't realize what would be required to get this project done. I've never done anything like this before (what I'm doing at work) and I didn't realize what resources would be needed before it became a critical issue. Of course, in the future, I will know better. For now though I'm under a real crunch to get this done right.

I guess what I'm saying is I can not practically afford to read through multiple manuals or documentation only to find out that it isn't suitable for my purpose. I turn to you guys in the hope that someone with experience will just say - "do this Jake. This is what you need."

Thanks for understanding and thanks for helping.
---------------------------

I guess I ought to be a little more descriptive of what I'm looking for. I think I was pretty broad and general in my first post.

I just need something simple I can set up on my machine that will allow someone else to download it from my local drive. I would set up the folder with a username and password and supply that to the person I wanted to access it. When they connected to my computer they would not be able to execute any old commands they felt like but would be limited to just a few actions. Looking at only the content I have chosen to provide to them (and not everything on the computer) - and downloading it from my computer to theirs. That's all.

Thanks

---

### Post by arrrghhh on 2011-05-24
SFTP is just SSH file transfer (basically).

So if you have SSH setup on your box, you can already use SFTP - it's pretty easy to setup, [here's a link](https://help.ubuntu.com/community/SSH) to the official Ubuntu SSH documentation.

But there's SFTP clients for every platform - not sure what OSX has, but in Windows I use WinSCP - great software.

Linux... natively supports it, they can use whatever they want...

---

### Post by ClientAlive on 2011-05-25
Right on. That link looks like a good place to start. Thank you.

Guess I was a little overwhelmed by the idea of what I wanted to do but maybe I can work it out after all.

---

### Post by Lars Noodén on 2011-05-25
A variation on the theme of SFTP is [SSHFS](http://packages.ubuntu.com/natty/sshfs).  It allows you to mount the other system as a directory and access it via any of the usual file management tools you are used to.

---

### Post by ClientAlive on 2011-05-25
> **Lars Noodén said:**
> A variation on the theme of SFTP is [SSHFS](http://packages.ubuntu.com/natty/sshfs).  It allows you to mount the other system as a directory and access it via any of the usual file management tools you are used to.


Right on. I'll have to check that out. I'm reading about openssh; and, so far, I like what I'm seeing. I'm just trying to figure out whether I'll be able to limit the client to a specific folder as opposed to everything on the computer. I'm sure you can.

The other thing is being able to allow multiple clients each with their own defined/ limited access. The first thing that came to mind was to make more than one sshd_config file for each person. Then, almost immediately, I had to throw that idea out. All that would do is trash my security and would not do what I'm trying to accomplish. If I had to guess, I would say the way to go about this is through permissions. More specifically, creating shared folders through the use of groups. This still seems a little shady to me though.

Ideally, if I could do it how I think would provide and optimal level of security, I would set it up somehow to where both a password and an SSH Key is used. Each client would have to first enter a password and then would be authenticated with the SSH Key. Or vice versa?

What do you think?? Am I on the right track?? Is there a better and/ or easier way?/

There's also this thing called Kerberos tickets but what I saw about that seems like (1) it requires additional equipment I don't have and (2) may kinda be overkill. I mean, I'm not in the CIA or anything. Yes, I want to be secure but . . .

What do you guys think about that??

---

### Post by Lars Noodén on 2011-05-25
> **ClientAlive said:**
> I'm just trying to figure out whether I'll be able to limit the client to a specific folder as opposed to everything on the computer. I'm sure you can.


That would be using SFTP with a [chroot](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts) jail.

---

### Post by ClientAlive on 2011-05-25
Where can if find the config file that tells openssh-server to start when the computer starts? I want to comment that out until I get everything configured correctly. Otherwise I have to run:

```

sudo /etc/init.d/ssh stop

```

every time the computer starts?

I mean, it does start up when the computer does doesn't it?

---

### Post by ClientAlive on 2011-05-25
> **Lars Noodén said:**
> That would be using SFTP with a [chroot](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts) jail.


:popcorn:

Well alritie then! Sweet! I really do wish you could see the smile on my face. This stuff is coool!

---

### Post by ClientAlive on 2011-05-25
> **Lars Noodén said:**
> That would be using SFTP with a [chroot](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts) jail.


Well hang on just a minute though. While I was reading at that link something else occurred to me . . .

It isn't just the content that needs to be addressed. People don't need to run any of the apps on my computer either. And they sure don't need access to some of the other devices like the cd/dvd drive or whatnot. Now, I anticipate I will either find out this is part of this chrooted thing or will at least be able to control some of that by the permissions I allow for the group?? But they need to be able to access the local disk - right? Now this is getting a little deeper.

I'm reading but am I reading all the right things??
-------------------

I don't mean "permissons I allow for the group" I mean when you go into: System > Administration > Users and Groups > Advanced Settings > _User Priveledges_

---

### Post by Lars Noodén on 2011-05-25
> **ClientAlive said:**
> I mean, it does start up when the computer does doesn't it?

Yes it should.

This is the old way to turn it on or off, but it works.  I'm not sure how the official 'upstart' way is.

```

# turn off
 update-rc.d ssh stop 20 0 1 2 3 4 5 6 S .

# restore to default
 update-rc.d ssh start 20 2 3 4 5 . stop 20 0 1 6 S .

```


PS. Chroot will prevent access to programs and anything else outside the chroot directory.

---

### Post by ClientAlive on 2011-05-25
> **Lars Noodén said:**
> Yes it should.

This is the old way to turn it on or off, but it works.  I'm not sure how the official 'upstart' way is.

```

# turn off
 update-rc.d ssh stop 20 0 1 2 3 4 5 6 S .

# restore to default
 update-rc.d ssh start 20 2 3 4 5 . stop 20 0 1 6 S .

```


PS. Chroot will prevent access to programs and anything else outside the chroot directory.

Ok. Cool on the "PS" part. That's good. But I'm not sure I understand the first part (about turning the thing off for now). Because I see a hash symbol I think this is something in a config file somewhere and not a command you run on on the command line? Is this in the /etc/ssh/sshd_config? I'd look at it right now but it's super late where I am and I have to get to bed. And are you also showing me how to turn it back on again later when I'm ready?

I need to crash out for tonight but I'll get back here tomorrow.

Thanks
---------------------

Edit: Yeah, I re-read what you wrote a couple times and thought about it, I think I can sort it out. I'll take a look around at things in the morn.

Thanks.

---

### Post by Lars Noodén on 2011-05-25
> **ClientAlive said:**
> Because I see a hash symbol I think this is something in a config file somewhere and not a {program} you run on on the {shell}? 


:)

Comments can be used anywhere.  That's why I try to refer to the activity as [shell scripting](http://www.gnu.org/software/bash/manual/bashref.html) and to the UI as the [shell](http://kb.iu.edu/data/agvf.html) rather than CLI.  But to answer the question, yes, both are ones you can enter in the [shell](http://www.bsdly.net/~lars/Lectures/Network-11-Shell-Script-Programming.odp), or as you called it, the "CLI".

An open secret is that there are no "commands" anywhere in Linux, just a bunch of programs that you can use separately, chain together (with pipes and redirects) or put into a script.

---

### Post by ClientAlive on 2011-05-25
I just noticed what it says in your signature. The first thing I thought was, mononucleosis (the kissing disease) - lol. I had to laugh. I followed the link though - didn't know there was something to do with computers that's called that. What a trip.


> **Lars Noodén said:**
> Yes it should.

This is the old way to turn it on or off, but it works.  I'm not sure how the official 'upstart' way is.

```

# turn off
 update-rc.d ssh stop 20 0 1 2 3 4 5 6 S .

# restore to default
 update-rc.d ssh start 20 2 3 4 5 . stop 20 0 1 6 S .

```


PS. Chroot will prevent access to programs and anything else outside the chroot directory.



I'm real sorry man but I just don't understand what this is I'm looking at (above). You know, I started with Linux maybe 6 or 7 wks ago. I've learned some (shell scripting? as you say in your other post) and I've had to edit a config file once to fix an error I was getting. I'll probably come across it as I read the manuals and whatnot, I guess.

> **Lars Noodén said:**
> :)

Comments can be used anywhere.  That's why I try to refer to the activity as [shell scripting](http://www.gnu.org/software/bash/manual/bashref.html) and to the UI as the [shell](http://kb.iu.edu/data/agvf.html) rather than CLI.  But to answer the question, yes, both are ones you can enter in the [shell](http://www.bsdly.net/~lars/Lectures/Network-11-Shell-Script-Programming.odp), or as you called it, the "CLI".

An open secret is that there are no "commands" anywhere in Linux, just a bunch of programs that you can use separately, chain together (with pipes and redirects) or put into a script.


I know it's kinda getting off the topic (which I don't personally mind, I kinda need that latitude at this point in my learning development) but . . .

Yeah, I haven't gotten as far as shell scripting (at least I didn't think so) but for some reason I'd got the idea that shell scripting is akin to programming. That the difference was you are using commands and things native to bash rather than arguments (such as if/ of or whatever). So I had the idea that a shell script was a text file that a person created and then pointed to it in some other existing config file to get it to run on the system. The way you put it makes it sound like anything you enter in the shell (bash, right?) is shell scripting. That would be different than the assumptions I've held. Maybe there's more than one thing that applies to the definition/ concept though.

I'd read several time too that "everything in Linux is a folder," and I've seen listing of folders and files for commands you enter in the shell (though I can't remember which directory that's in off the top of my head).

---

### Post by Lars Noodén on 2011-05-25
> **ClientAlive said:**
> ...
Yeah, I haven't gotten as far as shell scripting (at least I didn't think so) but for some reason I'd got the idea that shell scripting is akin to programming... The way you put it makes it sound like anything you enter in the shell (bash, right?) is shell scripting. ...

Yep. That's it.  If you try to "learn all the commands" then you will go nuts.  There are over 1400 files in /usr/bin alone.  

If you approach it as programming then it is a lot easier to pick up and less pressure.  It is also more likely that you'll start to automate some of the repetitive tasks.

I probably should have written it like this:

*turn off ssh permanently*
```

 update-rc.d ssh stop 20 0 1 2 3 4 5 6 S .

```

* restore ssh to default (on permanently)*
```

 update-rc.d ssh start 20 2 3 4 5 . stop 20 0 1 6 S .

```

And yes, absolutely everything is a file.

---

### Post by ClientAlive on 2011-05-25
> **Lars Noodén said:**
> Yep. That's it.  If you try to "learn all the commands" then you will go nuts.  There are over 1400 files in /usr/bin alone.  

If you approach it as programming then it is a lot easier to pick up and less pressure.  It is also more likely that you'll start to automate some of the repetitive tasks.

I probably should have written it like this:

[B]*turn off ssh permanently*
```

 update-rc.d ssh stop 20 0 1 2 3 4 5 6 S .

```

* restore ssh to default (on permanently)*
```

 update-rc.d ssh start 20 2 3 4 5 . stop 20 0 1 6 S .

```
[/B]
And yes, absolutely everything is a file.


Now I see something familiar and I know what I'm looking at. Thanks Lars.

> **Lars Noodén said:**
> 
. . .to automate some of the repetitive tasks.



Now you're talking my language. It would be way off in left field for me to bring this up but I'll shoot - I'm absolutely strangled right now with trying to find ways to do repetitive, daily, office admin tasks for my job. Stupid things that should be set up in a way that it takes only minutes to accomplish eat up half my day. They are things that need to be done (like managing contacts, sending email communication, dealing with documents so you don't have to do the same thing over from the beginning every time; and, of course, finding a way to share content with the people I work with (the ssh thing)). I'm trying to find a resource that has experience and wisdom with these things to sit down with me and point out the best ways to do these things but I keep running into a dead end with it. The business is taking off and I need to get this under control but what do I do? I can't seem to find anyone who can help me with that.

Like I mentioned, I know that is way off in left field from talking about ssh but I have a lot of little fires to put out and I don't know what else to do but bring it up wherever I talk to people. I don't say it the way I did here to everyone, but I am trying to reach out. I fear it is one element of starting a business that will make or break me. It scares me sometimes. Also, newbies tend to need the latitude to chase a few rabbits now and then - at least I have an excuse eh?  :D

Well, thanks for letting me get it off my chest at least. Thanks for all your advice and direction. I have a lot to go on now with the sftp thing and I don't think it's unreasonable to expect to have something running in the next few days - if I focus and do my homework.

I have to head out to the office for now but maybe I'll see you here again later on? In any case, thanks again man.

Sincerely,
Jake

---

