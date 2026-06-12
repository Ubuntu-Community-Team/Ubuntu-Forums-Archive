---
title: "Poll - Vote if you like this Central, Internal, Software Repository Implementation"
date: 2007-01-21
forum: The Cafe
---

### Post by dvarsam on 2007-01-21
Hello!

I have bumped into many posts where users ask for a Central, Internal Software Repository.
The idea is this:

1. You have a Network with 20 PCs. All of them are equipped with the Ubuntu OS.

2. The Ubuntu Update of Packages should be downloaded on one PC & the rest of the PCs on the Network should upgrade from the Repos of that _single_ PC.

So, instead of downloading the Ubuntu Updates 20 times (or one time, and then copy & paste all those download Packages 20 times), **I suggest the following**:

**1.** Currently, If you launch Synaptic Package Manager (from Menu, select "[color=blue]System\Administration \Synaptic Package Manager[/color]"), then from the Menu select "[color=blue]Settings\Preferences[/color]" & click on the **Tab** named "[color=blue]Files[/color]", you get the following window:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/1-4.png[/IMG]

**2.** The new version should be this one:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/2-3.png[/IMG]

_Note_:
In the above version, instead of all the Ubuntu upgrade packages be downloaded on the default folder "/var/cache/apt/archives", you can choose/create any folder you wish instead!

**3.** In the same way, the remaining 19 Networked PCs will have the following settings:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/3-4.png[/IMG]

_Note_:
1. That means their Ubuntu upgrade package folder is targeting/linking to "[color=blue]192.168.1.2.:/var/cache/apt/archives[/color]" [color=red]or[/color] any other folder you want!!!
And the target address "192.168.1.2" is of that 1rst PC that downloaded the Ubuntu upgrade packages!
Now, if the target folder is empty or contains some packages instead, then the Networked PCs download these files themselves, but save those new packages inside the above designated folder - i.e. the "[color=blue]192.168.1.2.:/var/cache/apt/archives[/color]".


Please vote if you like the current suggestion:

1. Yes, this is how I want this to work.
2. No, I don't like this - I prefer how things currently work.
3. I would like this to be implemented differently - please explain how...

Thanks.

---

### Post by Tomosaur on 2007-01-21
This is pretty much unnecessary if the **server** version is used in a thin-client network. Only the server ever needs to get updated, the other computers just use the server's software.

---

### Post by maniacmusician on 2007-01-21
sounds pretty cool

---

### Post by dvarsam on 2007-01-21
[QUOTE=Tomosaur]This is pretty much unnecessary if the **server** version is used in a thin-client network. Only the server ever needs to get updated, the other computers just use the server's software.[/QUOTE]

Sure, but in the case that I don't want to use a Server & prefer a bunch of Desktops instead, at least I _have_ a way to work around this...

In your scenario, you are _forcing_ the user/company to use a Server, while my implementation is NOT!
At the same time, even though you might be right, you can still _exclude_ **Step 3** above, & point/target all the Clients to the Server's Repo instead! 

Finally, you are also given a choice:
Instead of using the default Repo directory "[color=blue]/var/cache/apt/archives[/color]", you can use something like "[color=blue]/home/username/Repos[/color]"! This later one will be easier to visit compared to the Ubuntu's default one...

Not to mention, that **Synaptic** Package Manager is _protected_ by a **Password**, and in the case of the Server-Client scenario of yours, a Client user won't have the Password to be able to tamper/change the settings added by the Administrator (regarding the Repos the Client PC is supposed to use)...

Thanks.

P.S.> One way or another, this is a better implementation from what we currently have!

---

### Post by Tomosaur on 2007-01-21
> **dvarsam said:**
> Sure, but in the case that I don't want to use a Server & prefer a bunch of Desktops instead, at least I _have_ a way to work around this...

In your scenario, you are _forcing_ the user/company to use a Server, while my implementation is NOT!
At the same time, even though you might be right, you can still _exclude_ **Step 3** above, & point/target all the Clients to the Server's Repo instead! 

Finally, you are also given a choice:
Instead of using the default Repo directory "[color=blue]/var/cache/apt/archives[/color]", you can use something like "[color=blue]/home/username/Repos[/color]"! This later one will be easier to visit compared to the Ubuntu's default one...

Not to mention, that **Synaptic** Package Manager is _protected_ by a **Password**, and in the case of the Server-Client scenario of yours, a Client user won't have the Password to be able to tamper/change the settings added by the Administrator (regarding the Repos the Client PC is supposed to use)...

Thanks.

P.S.> One way or another, this is a better implementation from what we currently have!

What you're talking about is a server, so what's the problem? You're just making the whole thing a bigger waste of resources. A server by definition is something which serves data / processes things for clients. Any version of Ubuntu can be used as a server, it's just that the server edition is intended for people who are comfortable with the command line. Your way requires:
a) More work
b) More, bigger hardware on each computer.

The current way only requires a decent server computer.

---

### Post by sloggerkhan on 2007-01-21
I think this is a great idea for home users with moderate bandwidth.
I don't know about business users or people with servers, but if I have 3 PCs or so running ubuntu at home and they share a fairly slow connection (say 100 kb or so), this could simplify things a lot and help keep bandwidth from being tied up when they update separately.

---

### Post by runningwithscissors on 2007-01-21
I thought this was common practice on lots of network setups.

Not to mention, it also allows for testing of the packages with the machines comprising the local infrastructure, and should be the preferred method for deploying anything on a private network.

---

### Post by Polygon on 2007-01-21
sounds like a great idea, but isnt this the same as just setting up an apt server on your company network or whatever? or is it different in some way (as in the apt server doesn't download the packages from the ubuntu repos then lets all the computers on the network upgrade them selfs from the apt server or something?

---

### Post by Wolki on 2007-01-22
You need something like nfs sharing on the computer that's supposed to serve the apt archives anyway, so why not just mount that directory to /var/cache/apt/archives on each computer?
I'd imagine a solution like this to have some issues though (what if two computers want to update at the same time?), so an apt-proxy or something similar is likely a much better solution, and shouldn't be difficult to install.

---

### Post by mips on 2007-01-22
> **Tomosaur said:**
> What you're talking about is a server, so what's the problem? You're just making the whole thing a bigger waste of resources. A server by definition is something which serves data / processes things for clients. Any version of Ubuntu can be used as a server, it's just that the server edition is intended for people who are comfortable with the command line. Your way requires:
a) More work
b) More, bigger hardware on each computer.

The current way only requires a decent server computer.

Some just don't understand the definition of the word server... (and I'm not referring to you). Let it be.

---

### Post by Choad on 2007-01-22
sounds like a good idea to me. i doubt it would bloat anything at all significantly.

perhaps the input box for where to store the archives should be greyed out by default, so people dont go borking their systems by putting their files in a "better" place. just have a checkbox to make sure the user knows they shouldnt be messing with this unneccessarily.

---

### Post by dvarsam on 2007-01-22
[QUOTE=Tomosaur]What you're talking about is a server, so what's the problem?[/quote]

Why should we "force" anybody to install an Ubuntu Server OS edition?
But, sure, the 1rst PC which actually downloads the files is acting like a Server... 
And the rest of the PC get their updates from the 1rst PC (i.e. Server).
But the first PC is installed with Ubuntu Desktop OS - not Server Edition - even though it acts like a Server...

I thing that in your implementation of the Server-Client environment you are thinking of:

1. a Server PC
2. some Client **dummy** PCs - i.e. the Clients do not have any OS or HD installed - the Server contains their OS)

I am not talking about this...
And sure, if you are talking about this, you save a lot of Hardware resources.
But the Server has a lot of load to carry...
What if the 20 Client PCs, launch OOO writer simultaneously?
The Server would go down...!!! :)

[quote=Tomosaur]You're just making the whole thing a bigger waste of resources. A server by definition is something which serves data / processes things for clients. Any version of Ubuntu can be used as a server, it's just that the server edition is intended for people who are comfortable with the command line.[/quote]

Ok, so the 1rst PC - the Ubuntu Desktop OS, can act as a Server!
Some people don't like the command line...

**[color=blue]Alternatively, you could create a "symlink" on the 19PCs targeting the "var/cache/apt archives" folder of the 1rst PC.[/color]**
But I like things to work through GUI - not through Terminals or symlinks.

[quote=Tomosaur]Your way requires:

a) More work
b) More, bigger hardware on each computer.

The current way only requires a decent server computer.[/QUOTE]

**A.** In what way does it require "more work"?
It is a 2 step procedure & people/users like easy solutions!
You could also use the Terminal for doing this - if that is your problem (i.e. the settings are saved in a file & instead of doing this through GUI, you could edit the file instead...).

And if by referring to "more work" you mean programming, I don't give a damn how much coding it requires, I just want this to be easy on the users side...
_Everything_ in life requires "more work".
In Ubuntu we are always "working" for a:

1. Better kernel
2. Better gnome Environment
3. Better programs/packages
4. etc etc

Maybe we should quit those too - because they require "more work"... :)
And in your definition of "work", there is a limitation of how much we should "work"...
So, you are saying to the programmers - you have worked enough - stop working any more... :)

**B.** In what way does it require "More, bigger hardware on each computer"?
Oh, come on...
Say you don't like this idea or explain yourself...
So you are saying that I need a CPU of 3,6Ghz instead of the current 2,4GHz I have? :)

**In the same approach, mounting a Network Drive (i.e. Ethernet Hard Drive) available to all Networked PCs requires "More, bigger hardware on each computer"!** :)

Thanks.

---

### Post by ssam on 2007-01-22
apt-cacher and apt-proxy are tools that can do what you want, but they dont have simple GUI setups.

for the set up to be made even easier it should use avahi. the server would advertise the fact that it was caching packages, and all the other computers on the network would see this, and then be able to offer the user cached downloads when the ran apt-get, synaptic, update-manager, or app-install.

---

### Post by dvarsam on 2007-01-22
Hi & Thanks for your reply!

[QUOTE=Wolki]You need something like NFS sharing on the computer that's supposed to serve the apt archives anyway, so why not just mount that directory to /var/cache/apt/archives on each computer?[/quote]

Sure, IMHO it _is_ NFS sharing... (somebody correct me if I am wrong)
But in what way is is considered different than mounting a local directory on the rest 19 PCs which are in remote location?

I mean, that usually, you "mount" devices connected locally.
If you want to "mount" devices connected to some other Networked PC, you will definitely need NFS.
But isn't this what "Zero Configuration Networking" is supposed to be in Ubuntu v7.04 (Feisty)?
I assume that in Ubuntu v7.04, NFS is improved & installed by default...
So, all you would have to do is simply add "192.168.1.2.:/var/cache/apt/archives" in each networked PC.
In the case you don't like the GUI, then create a batch file which adds this line on the appropriate file...
Then all you have to do is run that batch file on every networked PC!
1+1=2 (this is very simple)

[quote=Wolki]I'd imagine a solution like this to have some issues though (what if two computers want to update at the same time?), so an apt-proxy or something similar is likely a much better solution, and shouldn't be difficult to install.[/QUOTE]

So, you are saying that a Proxy can serve many machines simultaneously?
**OR** the proxy will message the other Networked PCs that the files are currently "reserved" by a networked PC & that the remaining PC should try to update on a later time, when the files are considered "free" for use...?

But the later case could be "solved" if each Networked PC, copies those files internally & when finished updating, deletes those files...
Again, no multiple downloading of the same packages involved.

Thanks.

---

### Post by dvarsam on 2007-01-22
> **ssam said:**
> apt-cacher and apt-proxy are tools that can do what you want, but they don't have simple GUI setups.

I would like to play with how these programs work/function.
Is there a simple step-by-step tutorial on how can somebody setup **apt-cacher** or **apt-proxy**?

[quote=ssam]For the set up to be made even easier it should use avahi.
The server would advertise the fact that it was caching packages, and all the other computers on the network would see this, and then be able to offer the user cached downloads when the ran apt-get, synaptic, update-manager, or app-install.[/QUOTE]

So, how would someone use **avahi**.
I have to install that too?

Thanks.

---

### Post by Tomosaur on 2007-01-22
> **dvarsam said:**
> Why should we "force" anybody to install an Ubuntu Server OS edition?

Nobody's forcing anyone to install the server edition. I'm saying, this functionality already exists, you just haven't realized it. Ordinary Ubuntu can be made into a server, just like ordinary Windows (granted, in Windows it's a bit more difficult, but it can still be done).

> 
But, sure, the 1rst PC which actually downloads the files is acting like a Server... 
And the rest of the PC get their updates from the 1rst PC (i.e. Server).
But the first PC is installed with Ubuntu Desktop OS - not Server Edition - even though it acts like a Server...

I thing that in your implementation of the Server-Client environment you are thinking of:

1. a Server PC
2. some Client **dummy** PCs - i.e. the Clients do not have any OS or HD installed - the Server contains their OS)

I am not talking about this...
And sure, if you are talking about this, you save a lot of Hardware resources.
But the Server has a lot of load to carry...
What if the 20 Client PCs, launch OOO writer simultaneously?
The Server would go down...!!! :)

Yes, that's what I'm thinking of. You seem to be saying that one computer doing all the updates for each client computer is better than the clients just using the server's programs and data. Each to his own, but there's a reason why this isn't done, and that reason is that it requires more work (updating each computer manually) and means each computer needs to be able to handle all of the software. Currently, only the server needs to be able handle the workload - the desktop PCs can be pretty minimal.

> 
Ok, so the 1rst PC - the Ubuntu Desktop OS, can act as a Server!
Some people don't like the command line...

You don't need to touch the command line - like I said, this is all easily do-able in ordinary Ubuntu.

> 
**A.** In what way does it require "more work"?
It is a 2 step procedure & people/users like easy solutions!
You could also use the Terminal for doing this - if that is your problem (i.e. the settings are saved in a file & instead of doing this through GUI, you could edit the file instead...).

And if by referring to "more work" you mean programming, I don't give a damn how much coding it requires, I just want this to be easy on the users side...

Who said anything about programming? All of this stuff is **already there**, just not in the exact way you suggest. I'm not saying your idea is a bad idea, I'm just pointing out that it is unnecessary. If we were able to do it the way you suggested, it would still require more work, because you'd need to go around each computer and update it. The current way requires only one computer to be updated.

> 
**B.** In what way does it require "More, bigger hardware on each computer"?
Oh, come on...
Say you don't like this idea or explain yourself...
So you are saying that I need a CPU of 3,6Ghz instead of the current 2,4GHz I have? :)

**In the same approach, mounting a Network Drive (i.e. Ethernet Hard Drive) available to all Networked PCs requires "More, bigger hardware on each computer"!** :)

Thanks.
In your suggestion - every computer stores its own copy of the software. This requires bigger hardware. Each computer also needs to be able to run this software. Better processors. Each computer needs to be able to store the data required. Bigger hardware. In the current system, only ONE computer needs to handle the data and software. A computer which can do all of this can be expensive, yes, but you need to remember that the 'client' computers need only be very minimal. 

Now, I'm not trying to offend you or troll you or anything, I'm just trying to show you that this **already happens**, and the current implementation is more efficient and less costly than what you're proposing.

---

### Post by ssam on 2007-01-22
> **dvarsam said:**
> I would like to play with how these programs work/function.
Is there a simple step-by-step tutorial on how can somebody setup **apt-cacher** or **apt-proxy**?


[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)
[http://truehacker.blogspot.com/2006/11/create-ubuntu-repository-mirror-on-your.html](http://truehacker.blogspot.com/2006/11/create-ubuntu-repository-mirror-on-your.html)

> **dvarsam said:**
> 
So, how would someone use **avahi**.
I have to install that too?

Thanks.

[avahi]("http://avahi.org/") is installed by default in ubuntu, and i think feisty will have it on by default. it is a free implementation of [zeroconf]("http://www.zeroconf.org/"). it lets computers on a network choose names (like domain names), eg ssams_laptop.local or sams_music_server.local. and it allows the computers to tell each other what services they provide.

it is currently used for things like music sharing between itunes, rhythmbox, amarok etc, file sharing with [gshare]("http://yimports.com/~cpinto/projects/gnome/gshare/"), and a few other things.

---

### Post by dvarsam on 2007-01-22
Hello & thanks for your reply!

[QUOTE=ssam][https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)[/QUOTE]

I took a look at the link you provided & also at the following link:

[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)

Then bumped to this for "apt-cacher":

> To use this CGI you need a web server which supports CGI and a local directory with plenty of free space (100 - 300 Mbytes is usually adequate).

Also bumped to this for "apt-proxy":

> Because apt-proxy behaves as if it were a HTTP server with a full copy of the repositories you select, you can access the packages from other computers on your network...
...
If you are using a web proxy server (such as Squid)...

So, IF I get this right, in order to use either of the 2 programs I need to install a [b[Web Server[/b] first - i.e. LAMP (apache, mysql, php)?

Thanks.

---

### Post by Jussi Kukkonen on 2007-01-22
dvarsam, apt-proxy is a http-server (just a very specialized one), so nothing more is required. apt-cacher does need a web server, but definitely not a full lamp install.

---

### Post by dvarsam on 2007-01-22
[QUOTE=Tomosaur]Nobody's forcing anyone to install the server edition. I'm saying, this functionality already exists, you just haven't realized it. Ordinary Ubuntu can be made into a server, just like ordinary Windows (granted, in Windows it's a bit more difficult, but it can still be done).[/quote]

Ok.

[quote=dvarsam]I thing that in your implementation of the Server-Client environment you are thinking of:

1. a Server PC
2. some Client dummy PCs - i.e. the Clients do not have any OS or HD installed - the Server contains their OS)[/quote]

[quote=Tomosaur]Yes, that's what I'm thinking of. You seem to be saying that one computer doing all the updates for each client computer is better than the clients just using the server's programs and data.[/quote]

But you are forgetting here that most Users/Companie's Client PCs usually are equipped with Hard Drives, CPU, etc etc...
So, your implementation strategy applies only to Huge companies/corporations like HP, Compaq, Coca Cola, etc etc...

What about smaller sized companies?
OR even in a simple user case of a Home Ubuntu user (i.e. me & you), you are suggesting that I purchase a Server PC & some dummy PCs too?  
This is not the right approach in such user cases...!!!

[quote=Tomosaur]Each to his own, but there's a reason why this isn't done, and that reason is that it requires more work (updating each computer manually) and means each computer needs to be able to handle all of the software. Currently, only the server needs to be able handle the workload - the desktop PCs can be pretty minimal.[/quote]

I understand the point that each Client will have to update his Ubuntu PC manually, but I find it better compared to having to purchase dummies instead. 

[quote=Tomosaur]You don't need to touch the command line - like I said, this is all easily do-able in ordinary Ubuntu.[/quote]

Yes, in the case of a Central Server & dummy PCs, there won't be any command line typing on the Client's side...
But in my scenario, I am leaving this as an option too!
Whichever way users feel more comfortable...

[quote=Tomosaur]Who said anything about programming? All of this stuff is **already there**, just not in the exact way you suggest. I'm not saying your idea is a bad idea, I'm just pointing out that it is unnecessary. If we were able to do it the way you suggested, it would still require more work, because you'd need to go around each computer and update it. The current way requires only one computer to be updated.[/quote]

Sorry, I couldn't understand what the term "more work", you used, was referring to...
So, I assumed you meant, in order to implement this, more writing of code was required.
The term you used was very "vague"...

Yes, each Client user should update his PC separately - the IT department could send a PM to Clients to not forget to update their PCs.

[quote=Tomosaur]In your suggestion - every computer stores its own copy of the software. This requires bigger hardware. Each computer also needs to be able to run this software. Better processors. Each computer needs to be able to store the data required. Bigger hardware. In the current system, only ONE computer needs to handle the data and software. A computer which can do all of this can be expensive, yes, but you need to remember that the 'client' computers need only be very minimal.[/quote]

Yes, this is true!
However, this is the most common scenario used by most users/companies nowadays.
Excluding huge companies/corporations...
Don't forget the disadvantages involved when using dummy PCs.
E.g. - in case applications require big computing or lots of resources (e.g. architecture design of buildings or mechanic designs of machinery), there would be huge load on the Server time & the Clients would turn out slow...

[quote=Tomosaur]Now, I'm not trying to offend you or troll you or anything, I'm just trying to show you that this **already happens**, and the current implementation is more efficient and less costly than what you're proposing.[/QUOTE]

No problem.
But when you "reject" an idea, it is very important to state why in _full_ detail...
Also try not to use vague sentences like "it requires more work for this to be done".
I can translate "more work" at will - without being able to understand what you are talking about.
Thanks for your comments.
I still like my implementation idea though.

---

### Post by dvarsam on 2007-01-22
Hello & thanks for your reply!

[QUOTE=Jussi Kukkonen]dvarsam, apt-proxy is a http-server (just a very specialized one), so nothing more is required. apt-cacher does need a web server, but definitely not a full lamp install.[/QUOTE]

Thanks for clarifying this!
So, what parts of LAMP are required for using "apt-cacher"?

1. Apache
2. MySQL
3. PHP

Is it #1 above?

Thanks.

---

### Post by Jussi Kukkonen on 2007-01-22
> **dvarsam said:**
> 
Thanks for clarifying this!
So, what parts of LAMP are required for using "apt-cacher"?

1. Apache
2. MySQL
3. PHP

Is it #1 above?


Well, I've never used apt-cacher, but major dependencies like these are pretty much always mentioned in the documentation and web pages, and you already quoted the apt-cacher site front page: *"To use this CGI you need a web server which supports CGI and a local directory with plenty of free space* -- no mention of PHP or MySQL. Additionally, there's no reason for a program like that to require a real database or a web scripting language. I'd say it's a safe bet to say that PHP and MySQL are not required.

---

### Post by sloggerkhan on 2007-01-23
If it requires Apache it's pretty much beyond the scope of something for a small home network. (at least it will intimidate an average user.)

---

### Post by dvarsam on 2007-01-23
[QUOTE=sloggerkhan]If it requires Apache it's pretty much beyond the scope of something for a small home network. (at least it will intimidate an average user.)[/QUOTE]

Very True!
**We _need_ something easy!**

The solution suggested, requires:

1. Installing "apache",
2. I hope I don't have to configure "apache"... 
3. Installing "apt-cacher",
4. Configuring "apt-cacher" on the 1rst PC,
5. Configuring the Repos on the remaining Networked PCs.

Why should the user be messing with configuration? :confused:

IF you still believe that "apt-cacher" or other package is better, and I need to:

1. Configure Printer
2. Configure Scanner
3. Configure TV Card
4. Configure USB Webcam
5. Configure NFS or Samba
6. Set the "sources.list" file
7. Configure a Central Internal Repository for the Network
8. When packages are NOT available in ".deb" form, complile from source (don't forget installing appropriate libraries...)
9. Install & configure package "ntfs-3g" (including the configuration of "locales"), to keep a Central Repository for his files being used between Ubuntu < - > Windows.
10. etc etc ](*,) 

**Then we are not talking about a User Friendly OS, but we are discussing about a User "_Torture_" OS!**
For God's sake, keep things simple, people...!!!

Thanks.

---

### Post by Tomosaur on 2007-01-23
You say the user shouldn't have to configure things - well how exactly do you expect them to configure their apt to take packages from the main computer? Magic?

---

### Post by dvarsam on 2007-01-23
> **Tomosaur said:**
> You say the user shouldn't have to configure things - well how exactly do you expect them to configure their apt to take packages from the main computer? Magic?

Well, in my implementation strategy, all the user has to do is just type a _single_ line!
I don't understand why others want users/people to install some other packages & try solving "riddles" in order to cofigure those packages/programs...

How the hech is installing "apt-cacher" better than my implementation, when it already requires as a pre-requisite the installation of "apache"?
NOT only that, but you also need to "configure" the program "apt-cacher" too!
... which requires the user to "adopt/learn/use" a different style/notation for adding Repos inside his "sources.list" file!!!
So the user needs to learn/maintain 2 type of notations for the "sources.list" file - the Ubuntu "standard" one & the one "apt-cacher" uses!!!

My implementation strategy suggested only typing a _single_ line (look at **Step 3** please)...!!!
How is that in comparison with the other work-arounds suggested?
Thanks.

P.S.> How on Earth do you expect from a "Newbie" to even mess up with "apache" web server? !!! :roll:

---

### Post by dvarsam on 2007-01-23
[QUOTE=Tomosaur]You say the user shouldn't have to configure things - well how exactly do you expect them to configure their apt to take packages from the main computer? Magic?[/QUOTE]

It is impossible to use NO configuration at all!!!
We all know that & this is the simple _Truth_!
However, we should aim at keeping the configuration at "minimum"!!!
Thanks.

---

### Post by Tomosaur on 2007-01-23
> **dvarsam said:**
> It is impossible to use NO configuration at all!!!
We all know that & this is the simple _Truth_!
However, we should aim at keeping the configuration at "minimum"!!!
Thanks.
A minimum amount of configuration would be just letting the computer download from the net, regardless of how slow it is.

---

### Post by Jussi Kukkonen on 2007-01-23
> **dvarsam said:**
> Very True!
**We _need_ something easy!**

The solution suggested, requires:

1. Installing "apache",
2. I hope I don't have to configure "apache"... 
3. Installing "apt-cacher",
4. Configuring "apt-cacher" on the 1rst PC,
5. Configuring the Repos on the remaining Networked PCs.

Why should the user be messing with configuration? :confused:
...


I'm cutting the rest of your post as it was just hyperbole in my opinion. Dvarsam, I don't want to sound condescending, but it really looks like you are actively trying to not accept existing solutions to your problem... First, no-one has said apt-cacher requires apache. It requires a web server that can run CGI scripts. Second, you are conveniently forgetting about the simpler alternative: apt-proxy.

---

### Post by koenn on 2007-01-23
I second that. 
apt-proxy does exactly what the OP describes, can be installed just as easy as any other ubuntu package, and wouldn't require any post-install configuration if a reasonable default config were included in the package. at most, you'd neet to change the backend servers in the config files to something suitable for your country. Not too difficult if you consider that the target audience is "someone running/maintaining multiple ubuntu systems". 

On the client side, writing 1 line in sources.list is all it takes
Anybody can do that - how else would they have gotten those extra repos for codecs or whatever eye candy  available ? 
 (and maybe their are also GUI ways to do this - but i don't know as i don't use them).

---

### Post by aprice2704 on 2007-01-23
Sounds like a good idea to me. Using sFTP and zeroconf networking could make it even easier.

In the past I have also suggested adding bittottent support to apt to take the load off ubuntu servers when big updates come out. 

To those advocating apt-cache etc. -- fine if it works for you, but  we should strive for something non-geeks can use reliably. Sadly, that means GUI and autodiscovery.

Andy

---

### Post by koenn on 2007-01-24
> **aprice2704 said:**
> 
To those advocating apt-cache etc. -- fine if it works for you, but  we should strive for something non-geeks can use reliably. Sadly, that means GUI and autodiscovery.

Assuming apt-proxy goes under your "apt-cache etc", I really don't see how apt-proxy is any geekier than dvarsam's sollution. OK, you would have to download and install apt-proxy. Tick a checkbox in the GUI packet manager. And the clients would have to add a single line to sources.list, also possible by typing in Synaptic. I find using the advanced functions of my cell phone more geeky. 
And OK, if replacing archives.ubuntu.com by be.archives.ubuntu.com (or another country code) in the apt-proxy conf file, one could just default to archives.ubuntu.com, or add a small dialogue to the apt-proxy install script. 


On the other hand, there are a few tings in dvarsam's proposed sollution that are not entirely clear to me, and their sollution may just require the users to do some additional configuration - making it actually more complicated than simply installing apt-proxy ar so.

- to "share that folder" you'd need some kind of networking and filesharing protocols. I assume you'd prefer these to be availabel 'by default' and in a working order without any configuration or interverntion by any user. I 'm not convinced ithat this is possible, and if it is possible, I'm not convinced it's such a goog idea. I would not like any system to share stuff without me knowing it. 

- the 19 "clients" need at least read and write access to that 1 PC's shared folder with the downloaded packages. You'd probably need to create user accounts on that machine to allow them that access, or implement some other way of granting access to unauthenticated users without compromising security. I doubt that you can convince any Linux developer to allow unauthenticated remote access by default - Microsoft used to do such things, and even they are no longer convinced it's such a good idea. .

-20 pc's will be dropping downloaded packages in the shared folder, but the way apt works today, they will probably only be aware of the packages they downloaded themselves. You might  need to add additinal scripts, configuration, tweeking, ...to make each PC aware of what the others have downloaded already . Even if you'd provide a GUI front to let the user handle this, it would kinda take away the "just add a single line" advantage

-> that means GUI 
Ok for the GUI - it is helpfull sometimes - but after all it's just a wrap around real commands so you might as well say that what we need is a GUI wrapped around apt-proxy. Makes a lot more sense than re-inventing hot water. 

-> ... and autodiscovery.
I don't see (maybe I missed it) where dvarsam has any autodiscovery. I do see it expects 19 out of 20 users to know the repository-pc's IP address. So  that's a static adress ? manual network configuration then, no DHCP ? 
Or you could use DNS names in stead of IP addresses. Requires a DNS server on the local Network. Of course, installing and configuring a DNS server is easy, right ?


So, I'm not convinced how this idea is better that existing sollutions.

---

### Post by Quillz on 2007-01-24
Seems like a good idea, even for home users who want to keep one or two PCs synchronized and up-to-date.

---

### Post by lotacus on 2007-01-24
I like the idea of this however there is one cevit that arises: Not all PC's are the same and certainly not all the software/packages on PC's are the same. For instances, one pc may be running old libs necessary to support a certain application that hasn't been updated to support the newer library. This would cause dependancy issues. I ran into this problem myself. However, if you are managing a closely monitored closed environment network, in which all computers and software need to be the same, then yes, it would be a great idea. It is sort of like Microsoft's update services for Windows Server.

---

### Post by dvarsam on 2007-01-26
[QUOTE=Tomosaur]A minimum amount of configuration would be just letting the computer download from the net, regardless of how slow it is.[/QUOTE]

Sure!
And download the _same_ packages 1 time for _every_ Ubuntu Networked PC!
This is super!!! :)
**Viva Ubuntu**!
Thanks.

---

### Post by dvarsam on 2007-01-26
[QUOTE=koenn]Assuming apt-proxy goes under your "apt-cache etc", I really don't see how apt-proxy is any geekier than dvarsam's sollution. OK, you would have to download and install apt-proxy. Tick a checkbox in the GUI packet manager. And the clients would have to add a single line to sources.list, also possible by typing in Synaptic.[/quote]

Sure, but then IF you install apt-proxy, you will have to learn/maintain 2 types of **syntax**.

1. The one used in Ubuntu's "/etc/apt/sources.list"
2. The one used in "apt-cacher" or "apt-proxy" configuration files.

Why does a user have to learn/maintain 2 types of syntax?
I don't understand why...

[quote=koenn]And OK, if replacing archives.ubuntu.com by be.archives.ubuntu.com (or another country code) in the apt-proxy conf file, one could just default to archives.ubuntu.com, or add a small dialogue to the apt-proxy install script.[/quote]

IF this is the way to go, then somebody merge the syntax used between "apt-cacher" or "apt-proxy" & Ubuntu's "/etc/apt/sources.list" please...

[quote=koenn]On the other hand, there are a few things in dvarsam's proposed solution that are not entirely clear to me, and their solution may just require the users to do some additional configuration - making it actually more complicated than simply installing apt-proxy or so.

- to "share that folder" you'd need some kind of networking and filesharing protocols. I assume you'd prefer these to be available 'by default' and in a working order without any configuration or intervention by any user. I 'm not convinced that this is possible, and if it is possible, I'm not convinced it's such a good idea. I would not like any system to share stuff without me knowing it.[/quote]

But the release in Ubuntu v7.04 is promising "**Zero Configuration Networking**".
How do you expect the Ubuntu PC's to see each other if neither NFS nor Samba come pre-installed?
If neither of the 2 are pre-installed by default, then there must be some other way for Desktops/Clients to auto-detect each other... 

[quote=koenn]- the 19 "clients" need at least read and write access to that 1 PC's shared folder with the downloaded packages. You'd probably need to create user accounts on that machine to allow them that access, or implement some other way of granting access to unauthenticated users without compromising security. I doubt that you can convince any Linux developer to allow unauthenticated remote access by default - Microsoft used to do such things, and even they are no longer convinced it's such a good idea.[/quote]

Why would you need to create user accounts, while you could alternatively "mount" the 1 PC's shared folder in the remaining 19 networked PCs?
Adding a line in each of the 19 PCs, would be translated to:

**Please mount the Network Folder "/var/cache/apt/archives" on my PC please...**
No unauthenticated remote access involved, except mounting a shared folder...
Besides, as I have said before, only user "root" will be able to access Synaptic to do this...
It is safe, because only the Admin will have the "root" passwords... 

[quote=koenn]-20 pc's will be dropping downloaded packages in the shared folder, but the way apt works today, they will probably only be aware of the packages they downloaded themselves. You might  need to add additional scripts, configuration, tweeking, ...to make each PC aware of what the others have downloaded already. Even if you'd provide a GUI front to let the user handle this, it would kinda take away the "just add a single line" advantage.[/quote]

Why would the 20 PCs need to be aware of what packages they are dropping inside the Network shared folder inside the 1rst PC?
They don't need to remember what they have dropped in...
All they need to do, is when asked to perform an Ubuntu upgrade:

1. They check on the Internet what is the names (& latest versions) of packages to be updated
2. They check on (or "scan" on) the Shared Network Folder "/var/cache/apt/archives", whether some of the packages are already there.
3. They install packages that are already there, while they download packages that are NOT there.
4. For packages that were not available on the Shared Networked Folder & had to be downloaded separately, when the download is finished, they are saved/put in the Shared Networked Folder (i.e. "[color=blue]192.168.1.2.:/var/cache/apt/archives[/color]").

As simple as that!
I don't understand why do the 20 networked PCs need to "_only_ be aware of the packages they downloaded themselves", or even to be aware of _all_ the packages downloaded (by them or others)...
All the 20 networked PCs need to do is "scan/search" that 1rst PC's "var/cache/apt/archives" Folder with what packages are available...
Just keep things simple!

[quote=koenn]You might  need to add additional scripts, configuration, tweeking, ...to make each PC aware of what the others have downloaded already.[/quote]
Not at all!
You don't require every PC to search all the remaining 19 PC's repos...
You require that every PC search only the 1rst PC's Networked Shared Folder...
That is all...
A search on a single Networked Shared, user _specified_ folder.
And which folder is that?
The one you specify, when you add this line "[color=blue]192.168.1.2.:/var/cache/apt/archives[/color]".
The search is performed on the above user _specified_ folder.
NOT on the whole Hard Drive's contents...

[quote=koenn]-
Ok for the GUI - it is helpfull sometimes - but after all it's just a wrap around real commands so you might as well say that what we need is a GUI wrapped around apt-proxy. Makes a lot more sense than re-inventing hot water.[/quote]

Even though I can understand you, I disagree.
Users want the easy way...
BTW, I just tried to use "apt-cacher" (I chose this because I found an easy install HowTo) & got nowhere!!!
I will post this later - it is coming up...

[quote=koenn]-
I don't see (maybe I missed it) where dvarsam has any autodiscovery. I do see it expects 19 out of 20 users to know the repository-pc's IP address. So  that's a static adress ? manual network configuration then, no DHCP ? 
Or you could use DNS names in stead of IP addresses. Requires a DNS server on the local Network. Of course, installing and configuring a DNS server is easy, right ?[/quote]

Sure, that would either require:

1. Static IPs, or
2. Setting up DNS Names if you select the DHCP method 

But this already exists...
I like to go the Static way, but that is a choice of yours...


> So, I'm not convinced how this idea is better that existing solutions.

I need to congratulate you on the following:
THIS WAS THE _MOST_ EXPLANATORY ANSWER I HAVE SEEN IN THIS THREAD!!!
Bravo man, you helped me understand what was involved behind all this!
You seem to have a great knowledge in this area!
What I am missing is the "terminology" being involved here...
Your description of how things work, helped me contribute the way I envision this to work.

Hopefully we will converge to the same envisioning...
Thanks.

---

### Post by Nonno Bassotto on 2007-01-26
Don't if it has already been said, but you're looking for apt-proxy

---

### Post by dvarsam on 2007-01-26
[QUOTE=koenn]I second that. 
apt-proxy does exactly what the OP describes, can be installed just as easy as any other ubuntu package, and wouldn't require any post-install configuration if a reasonable default config were included in the package. at most, you'd neet to change the backend servers in the config files to something suitable for your country. Not too difficult if you consider that the target audience is "someone running/maintaining multiple ubuntu systems".[/quote]

Don't forget the diff _syntax_ used by apt-proxy, that a user is required to learn/maintain...

[quote=koenn]On the client side, writing 1 line in sources.list is all it takes
Anybody can do that - how else would they have gotten those extra repos for codecs or whatever eye candy available? 
 (and maybe their are also GUI ways to do this - but i don't know as i don't use them).[/QUOTE]

**_Facts of Ubuntu_:**
**1.** There is NO way for a new user to avoid editing the Ubuntu "/etc/apt/sources.list", if they want to install certain packages...
**2.** There is NO way for a new user to avoid editing the Ubuntu "/etc/fstab", if they want to create a permanent mount on another Hard Drive or Partition...
**3.** There is NO way for a new user to avoid installing & configuring NFS or Samba, if they want to Network their Ubuntu PCs with Windows PCs...

So, all I am suggesting is to "mount" the folder "/var/cache/apt/archives" of the 1rst PC on the remaining Networked Ubuntu PCs.
How demanding is that for the new user?

I am very happy, because "koenn" you have grasped the idea & you are helping me explain to others how this could work...!!!
Thanks.

---

### Post by dvarsam on 2007-01-26
[QUOTE=Nonno Bassotto]Don't if it has already been said, but you're looking for apt-proxy[/QUOTE]

So, as I promised, I decided to use your suggested "**apt-cacher**".
I chose that one (instead of "apt-proxy", because I found a nice HowTo... ...here: [http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)

According to the site [http://www.nick-andrew.net/projects/apt-cacher/](http://www.nick-andrew.net/projects/apt-cacher/):

“To use this CGI you need a Web Server which supports CGI & a local directory with plenty of free space (100 - 300 Mbytes is usually adequate).”

So, I decided NOT only to install "apache" but instead install:

1. Apache
2. MySQL
3. PHP
4. the rest of stuff required to setup a LAMP Server (what the heck, I thought why not install everything)...

After all the above, I was ready to install "**apt-cacher**"...
And so I did...

**STEP 2.** To test that it is installed correctly, you can try visiting the address below:

	[http://[color=blue]localhost](http://[color=blue]localhost)[/color]:3142/ or [http://[color=blue]LOCAL.IP](http://[color=blue]LOCAL.IP)[/color]:3142/

	(In my case, this would be: "http://[color=blue]192.168.1.2[/color]:3142".)

So, I open up a browser & type "http://[color=blue]192.168.1.2[/color]:3142".
And get this:

[quote=dvarsam]The connection was reset
The connection to the server was reset while the page was loading.
# The site could be temporarily unavailable or too busy. Try again in a few
    moments.

#   If you are unable to load any pages, check your computer's network
    connection.

#   If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.[/quote]

But, when I try typing "http://[color=blue]localhost[/color]:3142/" it works!!!

What is wrong in the first case?

Thanks.

---

### Post by Tomosaur on 2007-01-26
> **dvarsam said:**
> 
**_Facts of Ubuntu_:**
**1.** There is NO way for a new user to avoid editing the Ubuntu "/etc/apt/sources.list", if they want to install certain packages...

Yes there is.

> **2.** There is NO way for a new user to avoid editing the Ubuntu "/etc/fstab", if they want to create a permanent mount on another Hard Drive or Partition...
Yes there is. Granted, it's not obvious, but it IS there, and it IS easy to do.

> 
**3.** There is NO way for a new user to avoid installing & configuring NFS or Samba, if they want to Network their Ubuntu PCs with Windows PCs...

Yes there is.

Maybe you should try **using** Ubuntu before suggesting features which already exist.

---

### Post by koenn on 2007-01-26
> **dvarsam said:**
> 
I am very happy, because "koenn" you have grasped the idea & you are helping me explain to others how this could work...!!!
Thanks.
While I indeed thinkl I've grasped the idea, and my comments* might* make things more clear to others,  I don't actually want to be helping to convince others that what you're proposing is a "must have". 
let me repeat my opinion on your proposal:
> 
  I'm not convinced how this idea is better that existing solutions.
That means : there's a sollution for the problem you're trying to tackle. It's called apt-proxy. apt-proxy is not more complex than what you're proposing. 

Just to repeat some of the points that illustrate that your sollution is more complex than you care to admit:
1- it is meant for a network of multiple ( 20, in your example) PC's and requires either manual network configuration, or the use of DHCP + DNS. 
In the case of manual network configuration : how is that more simple and/or more easy user-friendly and/or  than installing apt-proxy through synaptic, (advisable but not strictly necessary : ) add an url for an ubuntu download server in apt-proxy.conf , and update  "Software Properties" (the GUI to sources.lst) with 1 url ?
In the case of DHCP and DNS : assuming DHCP is available out of the box, you still need to set up and configure a DNS server. 

whether this is done by the end-user or by some sysadmin who manages all PC's is besides the point : For the end-user you have in mind, manual network config is an impossible task (given that "they shouldn't have to do any configuration" - your words), for te sysadmin, well, it's up to him, but why would (s)he want to do manual network config or configure and run a DNS server if apt-config is readily available ? 

oh yeah, Zero Configuration Networking - that's the trick, right?
Do you actually know what it is ? For one, it is intended to kick in when no DHCP servers are found on the network. You or your sysadmin will have to disable to dhcp service on your router, for instance.  Might result in having to do some additional troubleshooting for devices that depend on dhcp and do not (yet) support network autoconfig, 

I appreciate you want things to be simple, but you can not make them simple by conveniently leaving out relevant facts. 

2- in addition to the network setup, you'd also have to setup and configure some sort of "access to a remote filesystem" - be it NFS, Samba, ftpmount or whatever. It's yet another thing your sysadmin would have to do, all of which is completely unnecessary with apt-proxy. 

Mind you, once it is setup, apt-proxy is completely transparant to the end-users - they don't even have to know that their Synaptic is using apt-proxy. Same goes for your sollution, but given the preparation needed to get it work, which is easier/ simpler/more user-friendly then ?


----------------------------------
I could actually leave it to that, but some of your comments to my post require a reply, so here we go :
---------------------------------

> Don't forget the diff syntax used by apt-proxy, that a user is required to learn/maintain...
I thought you said the config was going to be done by this admin person, since he only know the passwords. In any case, someone capable of setting up a network etc and all the preparations to make your sollution work, will probably not have to much trouble learning the 'syntax". It's just an URL, really. And I assume anyone using Ubuntu already mastered the immense differense in syntax between an email address and a web address, so i'm quite confident even a regualr user could cope with it. 


> So, all I am suggesting is to "mount" the folder "/var/cache/apt/archives" of the 1rst PC on the remaining Networked Ubuntu PCs.
Do it. take two pc's, and work on them until you can mount  "/var/cache/apt/archives" of the 1rst PC on the 2nd. Then come tell me it was easier than typing "http://be.archives.com/ubuntu" and "http://myserver/mypackages" - as you would when setting up apt-proxy. 

Possibly you'll expect this to be handled "automagically" - let the developer sort it out. Kinda cheap, but OK. But do it anyway - if only to find out what exactly is required in terms of permissions and user accounts - and how your users/systemadministrator is supposed to set them up. Maybe it's a piece of cake, maybe not, but untill you _know_, you can not just pretend that file permissions don't exist in a Linux filesystem, shared or not. 


> Quote:
[QUOTE]Originally Posted by koenn
-20 pc's will be dropping downloaded packages in the shared folder, but the way apt works today, they will probably only be aware of the packages they downloaded themselves. You might need to add additional scripts, configuration, tweeking, ...to make each PC aware of what the others have downloaded already. Even if you'd provide a GUI front to let the user handle this, it would kinda take away the "just add a single line" advantage.
(...)
All they need to do, is when asked to perform an Ubuntu upgrade:
(...)
2. They check on (or "scan" on) the Shared Network Folder "/var/cache/apt/archives", whether some of the packages are already there.

(...) All the 20 networked PCs need to do is "scan/search" that 1rst PC's "var/cache/apt/archives" Folder with what packages are available...
Just keep things simple![/QUOTE]

Apt does _not_ scan a folder to see what packages are there. Apt reads a file that contains a list of packages it has downloaded. That's why computer A will (probably) not be aware of packages that computer B - even if the store them in the same location. I say 'probably' because there might be ways of sharing that file as well, although then you'd have to deal with the possibility that 2 or more computers will want to write to it at the same time. That adds complexity to your sollution. Or you'd need additional tools to read the contents of the folder and update the index file. Yet more complexity to your sollution, or additional tweeking and configuring for the sysadmin. 

All that, while there are already simple, tested sollutions for yopur problem of having multiple pc's use the same downloaded packages ? Come on.

---

### Post by dvarsam on 2007-01-26
> **koenn said:**
> While I indeed think I've grasped the idea, and my comments* might* make things more clear to others,  I don't actually want to be helping to convince others that what you're proposing is a "must have".

Thanks.
[quote=koenn]let me repeat my opinion on your proposal:

That means: there's a solution for the problem you're trying to tackle. It's called apt-proxy. apt-proxy is not more complex than what you're proposing.[/quote]

IF apt-proxy can do this, why can't we replicate in some way what "apt=proxy" does in my suggestion?
There must be a better way to do this...

[quote=koenn]Just to repeat some of the points that illustrate that your solution is more complex than you care to admit:
1- it is meant for a network of multiple ( 20, in your example) PC's and requires either manual network configuration, or the use of DHCP + DNS.
In the case of manual network configuration: how is that more simple and/or more easy user-friendly and/or  than installing apt-proxy through synaptic, (advisable but not strictly necessary : ) add an url for an ubuntu download server in apt-proxy.conf , and update  "Software Properties" (the GUI to sources.lst) with 1 url ?
In the case of DHCP and DNS : assuming DHCP is available out of the box, you still need to set up and configure a DNS server.[/quote]

I don't understand this...
How come "apt-proxy" or "apt-cacher" are so capable of working under any environment:

a. DHCP. &
b. Static IPs

And we can't replicate in some way, how these work...
... so that we can embed them in my implementation strategy...?
Forget about DNS...
As I said, I have been trying to set up "apt-cacher" & currently I am "stuck"!!!
I thought that maybe I could solve things by setting up DNS through "bind9" & it is so hard... there is NO way I could make it work...
I was reading on this today, and now I have a headache...

[quote=koenn]whether this is done by the end-user or by some sysadmin who manages all PC's is besides the point:
a. For the end-user you have in mind, manual network config is an impossible task (given that "they shouldn't have to do any configuration" - your words),
b. for the sysadmin, well, it's up to him, but why would (s)he want to do manual network config or configure and run a DNS server if apt-config is readily available?/quote]

Sorry, but in my scenario, the Sysadmin could be a user... i.e. me!
IF manual network config involves to set Static IP or DHCP, that is not hard at all...
Unless you have in mind some other network config...?
Well in my scenario, as long as users set some Static IPs & add that magic line "[color=blue]192.168.1.2.:/var/cache/apt/archives[/color]" the "mounts" are going to be performed automatically. By the code involved in this.
The user won't do a thing!
How does "apt-proxy" or "apt-cacher" do it?
In some sort of way, they _also_ access a single Central Software Repository...
How is it possible for them to have access & my implementation not to?

[quote=koenn]oh yeah, Zero Configuration Networking - that's the trick, right?
Do you actually know what it is ? For one, it is intended to kick in when NO DHCP servers are found on the network. You or your sysadmin will have to disable to dhcp service on your router, for instance.  Might result in having to do some additional troubleshooting for devices that depend on dhcp and do not (yet) support network autoconfig, 

I appreciate you want things to be simple, but you can not make them simple by conveniently leaving out relevant facts.[/quote]

I thought of Zero Configuration Networking to be the following:

1. I have a Router.
2. I plug one PC on the Router
3. I plug another PC on the Router.
Tada... these 2 PCs can see each other!
And when you select from the Menu "Places\Network Servers..." an icon will appear for each computer that exists on my Network!
I don't care if that involves NFS or Samba be pre-installed by default, but this is what I think "Zero Configuration Networking" should be!
I guess that the term "Zero Configuration Networking" & the description for the work that it does is misleading...!!!
Users want easy stuff...
I truly hope that it does something like that...

[quote=koenn]2- in addition to the network setup, you'd also have to setup and configure some sort of "access to a remote filesystem" - be it NFS, Samba, ftpmount or whatever. It's yet another thing your sysadmin would have to do, all of which is completely unnecessary with apt-proxy.[/quote]

Well, "apt-proxy" should work in some similar manner...
How does "apt-proxy" access some Central Network Sofware Repository if it isn't through Samba or NFS?
What kind of "voodoo" does it use, that we can't use?

[quote=koenn]Mind you, once it is setup, apt-proxy is completely transparent to the end-users - they don't even have to know that their Synaptic is using apt-proxy. Same goes for your solution, but given the preparation needed to get it work, which is easier/ simpler/more user-friendly then?[/quote]

If it can be done in the same manner as "apt-proxy", then my solution would be better!

[quote=koenn]----------------------------------
I could actually leave it to that, but some of your comments to my post require a reply, so here we go :
---------------------------------

I thought you said the config was going to be done by this admin person, since he only know the passwords. In any case, someone capable of setting up a network etc and all the preparations to make your solution work, will probably not have to much trouble learning the 'syntax". It's just an URL, really. And I assume anyone using Ubuntu already mastered the immense differense in syntax between an email address and a web address, so i'm quite confident even a regualr user could cope with it.[/quote]

I checked on the syntax "apt-cacher" uses & it is NOT hard at all...
Inside the file "/etc/apt/sources.list", you need to replace lines like:

[color=blue]deb [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) unstable main contrib non-free[/color]

to: 

[color=blue]deb http://[/color][color=red]localhost:3142[/color][color=blue]/ftp.au.debian.org/debian unstable main contrib non-free[/color]

Note: where "localhost" = your Server's IP

But IF I use the IP version of it, I get errors all over!!!
And none of the "sources" work...

[quote=koenn]Do it. take two pc's, and work on them until you can mount  "/var/cache/apt/archives" of the 1rst PC on the 2nd. Then come tell me it was easier than typing "http://be.archives.com/ubuntu" and "http://myserver/mypackages" - as you would when setting up apt-proxy.
Possibly you'll expect this to be handled "automagically" - let the developer sort it out. Kinda cheap, but OK. But do it anyway - if only to find out what exactly is required in terms of permissions and user accounts - and how your users/systemadministrator is supposed to set them up. Maybe it's a piece of cake, maybe not, but untill you _know_, you can not just pretend that file permissions don't exist in a Linux filesystem, shared or not. 

I understand this, but again I explained earlier how this could be done...
Something similar to how "apt-proxy" does this...

[quote=koenn]Apt does _not_ scan a folder to see what packages are there. Apt reads a file that contains a list of packages it has downloaded. That's why computer A will (probably) not be aware of packages that computer B - even if the store them in the same location. I say 'probably' because there might be ways of sharing that file as well, although then you'd have to deal with the possibility that 2 or more computers will want to write to it at the same time. That adds complexity to your solution. Or you'd need additional tools to read the contents of the folder and update the index file. Yet more complexity to your solution, or additional tweaking and configuring for the sysadmin. 

All that, while there are already simple, tested solutions for your problem of having multiple PC's use the same downloaded packages ? Come on.[/QUOTE]

Maybe we can embed "apt-proxy" in my implementation & when typing the things I have suggested, "apt-proxy" implements these in the background...
There must be a workaround on this.
How does "apt-proxy" scan a folder to see what packages are there?
How does "apt-proxy" reads a file that contains a list of packages that "apt" has downloaded?
One way or another, there is a solution to this...

Thanks

---

### Post by dvarsam on 2007-01-26
Hello again!

As I said before, I decided to try your suggested "**apt-cacher**".
So, I have installed:

1. Apache
2. MySQL
3. PHP
4. the rest of stuff required to setup a LAMP Server (what the heck, I thought why not install everything)...
5. **apt-cacher**

To test that "apt-cacher" is fine, I open up a browser & type "http://192.168.1.2:3142".
And get this:

> The connection was reset
The connection to the server was reset while the page was loading.
# The site could be temporarily unavailable or too busy. Try again in a few
moments.
# If you are unable to load any pages, check your computer's network
connection.
# If your computer or network is protected by a firewall or proxy, make sure
that Firefox is permitted to access the Web.

At the same time, IF I try typing "http://localhost:3142/" it works!!!

_Question 1_:
What is wrong in the first case?
Does this mean that I have to setup DNS?

Then, I went on the networked PC's "/etc/apt/sources.list" file & changed every line as:

deb [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) unstable main contrib non-free

to:

deb [http://[color=red]localhost:3142/](http://[color=red]localhost:3142/)[/color]ftp.au.debian.org/debian unstable main contrib non-free

Note: where "localhost" = your Server's IP

I then launch Synaptic Package Manager on the Networked PCs & click on the button "Reload".
And Synaptic Package Manager, unfolds 46 errors!!!

I guess that when I put/use the IP version in between, I get errors all over!!!
And none of the "sources" work...

_Question 2_:
So what do I do?
IF I can't use the IP notation (i.e. 192.168.1.2:3142), what notation do I use instead?
A "localhost:3142"?
Would that be possible?
Do I need to "restart" any programs?
I.E. "apache" or "apt-cacher"?
And how will a Networked PC know that "localhost:3142" links/points to "192.168.1.2:3142"?
So, I need DNS now?
I need to setup a "LAN DNS Server"?
You call that easy?

Please help!!!

Thanks.

P.S.> I was reading about LAN DNS Server Setup all afternoon, now I have a headache...
It is very very hard (if not impossible) to setup a DNS Server...
There are NOT many examples out there & I don't see any explanatory step-by-step threads available...
IF this is the case, then forget about "apt-cacher"!!!
I desperately need your help guys... :(

---

### Post by koenn on 2007-01-27
OK then, one for the road.

> I don't understand this...
How come "apt-proxy" or "apt-cacher" are so capable of working under any environment:

a. DHCP. &
b. Static IPs
because the are designed to work in a TCP/IP network, and how the network itself functions doesn't matter to them. Explaining this in detail would take a while, so I'm not going to. A rough methaphor could be that a car does not need to know how the road was build to be capable of transporting people/goods from one point to another. Find a tutorial on TCP/IP if you really want to know. 

> How does "apt-proxy" or "apt-cacher" do it?
In some sort of way, they also access a single Central Software Repository...
How is it possible for them to have access & my implementation not to?
They run on the machine that has the repository, and have a user account on that machine to be allowed access. Clients do not need to access the repository directly, they talk to apt-proxy/apt-cache, using http. It's called a client-server architecture. Try wikipedia, they explain all about it. http is a networking protocol, and an open standard. Same thing apt-get uses, and firefox

> Well, "apt-proxy" should work in some similar manner...
How does "apt-proxy" access some Central Network Sofware Repository if it isn't through Samba or NFS?
What kind of "voodoo" does it use, that we can't use?
It doesn't use voodoo. see previous paragraph . Voodoo might work, but is harder to implement because it requires Soulscript and spiritinthesky.deb.


> How does "apt-proxy" reads a file that contains a list of packages that "apt" has downloaded?
Apt downloads from the apt-proxy cache; if a package is not already in the cache, apt-proxy itself will download it from the download servers on the internet. That's more or less the definition of a proxy. Anyway, apt-proxy knows what it has downloaded and what's in its cash, creates a Packages.gz file for it and presents that to any apt (your 20 clients) that wants to know what packages are available. It's pretty much the same way a real Ubuntu / Debian repository works. That makes it such an elegant sollution : it builds beatifully on already existing technology, increasing the functuonality with a few simple additions. Gotta love it. 



> I thought of Zero Configuration Networking to be the following:

1. I have a Router.
2. I plug one PC on the Router
3. I plug another PC on the Router.
Tada... these 2 PCs can see each other!

That's what could happen, either with Zero Configuration Networking or with DHCP. The only difference would be in the inner workings of the network, something you as a 'lets keep it simple, people' kinda user don't want to know about. Fine with me. 

> And when you select from the Menu "Places\Network Servers..." an icon will appear for each computer that exists on my Network!
Funny how my Dapper Drake already does that. Must be something Samba and/or Nautilus - There's no Zero Configuration Networking in Dapper, at least that I know of.

>  ... but this is what I think "Zero Configuration Networking" should be!
I guess that the term "Zero Configuration Networking" & the description for the work that it does is misleading...!!!
Users want easy stuff...
I truly hope that it does something like that...
I guess you glanced at a description of Zero Configuration Networking, didn't understand it, thus dismissed it as misleading and too complex for the average user, the average user being, of course, you. 
Taking your wishes for facts, then blame the facts that they're not quite the same as what you wished usually is not very productive, I find. but I could be wrong. 

> And how will a Networked PC know that "localhost:3142" links/points to "192.168.1.2:3142"?
So, I need DNS now?
I need to setup a "LAN DNS Server"?
You call that easy?
localhost:3142 points to 127.0.0.1:3142, and any pc with standard TCP/IP knows that. 
For any other address (other than 127.0.0.1, that is) to translate to a hostname, you need some sort of address resolution, usually DNS, but you can also edit /etc/hosts on every computer of the network in stead of running a DNS server. 
I never said that setting up DNS would be easy. I just said ***your* sollution might require it **(in certain circumstances - see my previous post). And no, Zero Configuration Networking is not meant to set up a DNS server for you. 


> If it can be done in the same manner as "apt-proxy", then my solution would be better!
If it can be done in the same manner as "apt-proxy", then your solution would be apt-proxy

> 
Maybe we can embed "apt-proxy" in my implementation & when typing the things I have suggested, "apt-proxy" implements these in the background...
So you want a GUI front-end to apt-proxy, really. Fair enough.

---

### Post by dvarsam on 2007-01-27
> **koenn]OK then, one for the road.

because the are designed to work in a TCP/IP network, and how the network itself functions doesn't matter to them. Explaining this in detail would take a while, so I'm not going to. A rough methaphor could be that a car does not need to know how the road was build to be capable of transporting people/goods from one point to another. Find a tutorial on TCP/IP if you really want to know.[/quote]

I think I can understand how they work...
In some sort of way they "hijack" the "apt-get" mechanism, and sniff all localhost (i.e. 127.0.0.1) "public" messages sent over the network through TCP-IP...
And then they "filter" out the messages they don't care about...
And they function/work with the messages they should...
Am I right?
It must be some similar way like this...
I can't think of anything else...

[quote=koenn]They run on the machine that has the repository, and have a user account on that machine to be allowed access. Clients do not need to access the repository directly, they talk to apt-proxy/apt-cache, using http. It's called a client-server architecture. Try wikipedia, they explain all about it. http is a networking protocol, and an open standard. Same thing apt-get uses, and firefox[/quote]

For "apt-cacher" & "apt-proxy" to be able to create user accounts on the rest of the Networked PCs, it would mean that _all_ Networked PCs should be up & running when a user decides to install either of the above on the **Server** PC... isn't that right?
I.E. You can't create a user account on a Client PC that is NOT up & running, can you?

Unless "apt-cacher" or "apt-proxy" need to _also[/b] be installed on [u]every_ Client too!
IF the later is true, then maybe that is the reason why "apt-cacher" can NOT do the trick on my Client PC...
Maybe I need to install "apt-cacher" on the Client PCs too!

[quote=koenn]It doesn't use voodoo. see previous paragraph . Voodoo might work, but is harder to implement because it requires Soulscript and spiritinthesky.deb.[/quote]

lol... :)
True!

[quote=koenn]Apt downloads from the apt-proxy cache said:**
> 

OK, but I have some suggestions for improvements of "apt-cacher"...
I will give them in detail, in the end of this post!

[quote=koenn]That's what could happen, either with Zero Configuration Networking or with DHCP. The only difference would be in the inner workings of the network, something you as a 'lets keep it simple, people' kinda user don't want to know about. Fine with me.

Then this is very cool!
I can't wait for this...

[quote=koenn]Funny how my Dapper Drake already does that. Must be something Samba and/or Nautilus - There's no Zero Configuration Networking in Dapper, at least that I know of.[/quote]

I guess your Dapper is applying some secret voodoo...!!! :)
Just joking.
Probably it is what you said...

[quote=koenn]I guess you glanced at a description of Zero Configuration Networking, didn't understand it, thus dismissed it as misleading and too complex for the average user, the average user being, of course, you. 
Taking your wishes for facts, then blame the facts that they're not quite the same as what you wished usually is not very productive, I find. but I could be wrong.[/quote]

I guess that now that you clarified that it includes my rough sketch...
... then I must say that I was wrong when claiming that its project's name (i.e. "Zero Configuration Networking) is misleading...
Please accept my apologies for that.... :oops:

[quote=koenn]localhost:3142 points to 127.0.0.1:3142, and any PC with standard TCP/IP knows that. 
For any other address (other than 127.0.0.1, that is) to translate to a hostname, you need some sort of address resolution, usually DNS, but you can also edit /etc/hosts on every computer of the network in stead of running a DNS server. 
I never said that setting up DNS would be easy. I just said ***your* sollution might require it **(in certain circumstances - see my previous post). And no, Zero Configuration Networking is not meant to set up a DNS server for you.[/quote]

Oh my goodness!
Sorry I did NOT know that...
And I thought that localhost = my local PC's IP address (i.e. 192.168.1.2)...
That was why it was not working!!! :oops:
From what I have found, DNS is very hard (if not impossible) to setup...
So I guess that when I am asked to replace the sources.list's" lines from:

deb [http://archive.ubuntu.com/ubuntu/edgy](http://archive.ubuntu.com/ubuntu/edgy) main restricted

to:

deb [http://[color=blue]](http://[color=blue])[LOCAL.IP]:3142/[/color]archive.ubuntu.com/ubuntu/ edgy main restricted

**OR**:

Replace:

deb [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) unstable main contrib non-free

with: 

deb [http://](http://)[color=blue]yourcache.example.com:3142/[/color]ftp.au.debian.org/debian unstable main contrib non-free

Why can't it work?
I get the [color=red]Error 111[/color] output!!!

I have tried using the following notation/syntax inside "/etc/apt/sources.list" file on the Clients side:

1. deb [http://[color=blue]localhost:3142/](http://[color=blue]localhost:3142/)[/color]ftp.au.debian.org/debian 
2. deb [http://[color=blue]127.0.0.1:3142/](http://[color=blue]127.0.0.1:3142/)[/color]ftp.au.debian.org/debian 
3. deb [http://[color=blue]](http://[color=blue])[localhost]:3142/[/color]ftp.au.debian.org/debian 
4. deb [http://[color=blue]](http://[color=blue])[127.0.0.1]:3142/[/color]ftp.au.debian.org/debian 
 
None of them seem to work!
They all create the  [color=red]Error 111[/color] output!!!

[quote=koenn]If it can be done in the same manner as "apt-proxy", then your solution would be apt-proxy[/quote]

:)
Then I guess in an improved way...

[quote=koenn]So you want a GUI front-end to apt-proxy, really. Fair enough.[/QUOTE]

That would help!
[u]Let me suggest the following improvements[u]:
(Note: since i am currently trying to configure "apt-cacher" I can only suggest improvements on that one...)

1. On the Client's side, inside the "/etc/apt/sources.list" file:

Instead of having to change every single occurrence from notation:

deb [http://ftp.au.debian.org/debian](http://ftp.au.debian.org/debian) unstable main contrib non-free

to notation: 

deb [http://](http://)[color=blue]yourcache.example.com:3142/[/color]ftp.au.debian.org/debian unstable main contrib non-free

Implement this improved one:

A _single_ line like this:

deb [http://localhost:3142/apt-cacher](http://localhost:3142/apt-cacher)

It is always better to have to type 1 _single_ line in there, than to have to edit _every_ single line in there...
Note: in my "/etc/apt/sources.list" file, I have 30 lines in total...
It "sucks" when I have to edit each line separately in there...
Why can't we implement this?
And since you are talking about adding a GUI to the "apt-cacher" or "apt-proxy"...

And the GUI I proposed in "Step 2" of my suggested implementation strategy:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/2-3.png[/IMG]

Instead of: "[color=blue]Save all downloaded packages in the following folder
Location: /var/cache/apt/archives[/color]"

You could have: [color=blue]Use the following Repo instead of "/var/cache/apt/archives"
Repo: deb [http://localhost:3142/apt-cacher](http://localhost:3142/apt-cacher)[/color]

And the above command be _disabling_ the Client PC's Repos (in this manner NO editing is performed on any Client's Repos (i.e. The Client's Repos & the Server's Repos have _identical_ contents) & the above line links/targets the Server's Repos!!!

In this manner, you also eliminate the case where a User might make a typo error when he edits the "/etc/apt/sources.list" file on the Clients side...
Because it is easier to check whether a _single_ line has a typo error, compared to checking _every_ single line in a total of 30 lines (you don't want to be searching for a "typo/needle in a stack of hay" - do you?).

What do you think of that?
In this way, we have a very simplistic GUI & a better method to address the editing of the Client PCs.

Thanks.

P.S.> BTW - any ideas on how to fix my problem?
What am I doing wrong in setting up "apt-cacher" on the Clients side?

---

### Post by Tomosaur on 2007-01-27
Dvarsam, please just give up. Your 'thing' has evolved from something which already exists, to something which doesn't do what you originally set out to do. I don't understand this part:
> 
And the above command be disabling the Client PC's Repos (in this manner NO editing is performed on any Client's Repos (i.e. The Client's Repos & the Server's Repos have identical contents) & the above line links/targets the Server's Repos instead!!!

If the server and the client have identical stuff, then **what is the point**?

The existing solutions are **far easier, more efficient, and generally just better** than what you are proposing. All you need is a **server** and a bunch of **thin clients**.

---

### Post by RAV TUX on 2007-01-27
> **dvarsam said:**
> Hello!

I have bumped into many posts where users ask for a Central, Internal Software Repository.
The idea is this:

1. You have a Network with 20 PCs. All of them are equipped with the Ubuntu OS.

2. The Ubuntu Update of Packages should be downloaded on one PC & the rest of the PCs on the Network should upgrade from the Repos of that _single_ PC.

So, instead of downloading the Ubuntu Updates 20 times (or one time, and then copy & paste all those download Packages 20 times), **I suggest the following**:

**1.** Currently, If you launch Synaptic Package Manager (from Menu, select "[COLOR=blue]System\Administration \Synaptic Package Manager[/COLOR]"), then from the Menu select "[COLOR=blue]Settings\Preferences[/COLOR]" & click on the **Tab** named "[COLOR=blue]Files[/COLOR]", you get the following window:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/1-4.png[/IMG]

**2.** The new version should be this one:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/2-3.png[/IMG]

_Note_:
In the above version, instead of all the Ubuntu upgrade packages be downloaded on the default folder "/var/cache/apt/archives", you can choose/create any folder you wish instead!

**3.** In the same way, the remaining 19 Networked PCs will have the following settings:

[IMG]http://i69.photobucket.com/albums/i58/dvarsam/3-4.png[/IMG]

_Note_:
1. That means their Ubuntu upgrade package folder is targeting/linking to "[COLOR=blue]192.168.1.2.:/var/cache/apt/archives[/COLOR]" [COLOR=red]or[/COLOR] any other folder you want!!!
And the target address "192.168.1.2" is of that 1rst PC that downloaded the Ubuntu upgrade packages!
Now, if the target folder is empty or contains some packages instead, then the Networked PCs download these files themselves, but save those new packages inside the above designated folder - i.e. the "[COLOR=blue]192.168.1.2.:/var/cache/apt/archives[/COLOR]".


Please vote if you like the current suggestion:

1. Yes, this is how I want this to work.
2. No, I don't like this - I prefer how things currently work.
3. I would like this to be implemented differently - please explain how...

Thanks.

My apology if I mis-understand what you are trying to convey but doesn't this already exist here:

**[[B]klik** - Linux Software Download]("http://klik.atekon.de/")

[/B]> [IMG]http://klik.atekon.de/dw/mission.jpg[/IMG]  
     To quickly prepare your system for klik, install the klik client (NOT as root):     wget klik.atekon.de/client/install -O -|sh         and follow instructions on screen. (K)Ubuntu users, please first      run               sudo apt-get install binutils libstdc++5 rpm gnome-about    **Latest klik-able applications** [[IMG]http://www.kubuntu.org/images/rss.png[/IMG]]("http://klik.atekon.de/rss.php")


> **What is klik**

 	   	    **From klik**

 	     	    	    	     	    *klik aims to become the most simple way to let a user run and use Linux software, without even a need for "installing" the application.* 
klik is a system which creates self-contained packages of applications as a single file. That application file then can run from anywhere (even from an USB thumbdrive or CD-RW), or be copied to a different Linux computer (32bit only for now) and used there. 
klik "ingredients" are downloadable from the web and are converted into the respective self-contained package with a single click, even while running a Live-CD. 
Because one software package is always exactly just one compressed cmg file, you can always delete software packages without any problems for other software. Because you can save cmg files everywhere, this solution is very flexible. 
**klik Is** 
 [LIST]
[*] An easy way to download and run software -- without installing it
[*] 1 File = 1 Application
[*] Safe to use -- it never interferes with your existing system
[*] An easy way to distribute applications
[*] Able to run in user space without root/sudo[/LIST] **klik Is Not** 
 [LIST]
[*] A package management system. It doesn't strive to replace apt-get, dpkg, rpm, yum, apt4rpm, portage, smart, autopackage or what-have-you.
[*] klik is not a Microsoft Windows application[/LIST] *(klik is currently to be regarded as "usable alpha" quality, meaning: not all packages work for all distros/users. But **if** a package works, it works normally quite well. Try it, and don't give up after the first failure -- try another one then.)*
[http://klik.atekon.de/wiki/index.php/What_is_klik](http://klik.atekon.de/wiki/index.php/What_is_klik)

---

### Post by RAV TUX on 2007-01-27
> **How to use klik**

                **From klik**

                                            **Table of contents** showTocToggle("show","hide")[[showhide]("http://javascript%3Cb%3E%3C/b%3E:toggleToc%28%29")]  [1 Short instructions]("http://klik.atekon.de/wiki/index.php/How_to_use_klik#Short_instructions")

 [2 Live chat support]("http://klik.atekon.de/wiki/index.php/How_to_use_klik#Live_chat_support")

 [3 Long description with screenshots]("http://klik.atekon.de/wiki/index.php/How_to_use_klik#Long_description_with_screenshots")

   [3.1 Install prerequisites]("http://klik.atekon.de/wiki/index.php/How_to_use_klik#Install_prerequisites")
[3.2 Start the installation]("http://klik.atekon.de/wiki/index.php/How_to_use_klik#Start_the_installation")
[3.3 Firefox]("http://klik.atekon.de/wiki/index.php/How_to_use_klik#Firefox")
[3.4 Start using klik]("http://klik.atekon.de/wiki/index.php/How_to_use_klik#Start_using_klik")

 
 

** Short instructions **[LIST]
[*] Check in [the FAQ]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_other_requirements.3F") whether you have the right dependancies installed to run klik:[/LIST][LIST]
[*] If you are using Ubuntu or Kubuntu, prepare your system with[/LIST]sudo apt-get install binutils libstdc++5 rpm gnome-about dialog[LIST]
[*] Install the klik client:[/LIST]wget klik.atekon.de/client/install -O - | sh[LIST]
[*] Follow the instructions that pop up on your screen.
[*] **Close your browser, and open it again.** Now, klik links like klik://xvier should work.[/LIST]** Live chat support **

 There is [Online support]("http://klik.atekon.de/wiki/index.php/Online_support") via IRC. 
 
** Long description with screenshots **

 This is a long desciption with screenshots. If the above short description works for you, you do not need the long description. 
 
** Install prerequisites **

 If you are running (K)Ubuntu, open a konsole and enter 
 sudo apt-get install binutils libstdc++5 rpm gnome-about kdelibs-bin
gnome-about is there in order to ensure that you have all libraries for running Gnome/GTK-based applications. 
kdelibs-bin is optional in order to ensure that you have all libraries for running QT/KDE based applications. 
[IMG]http://img204.imageshack.us/img204/4839/kubuntu15jn.jpg[/IMG] 
 
** Start the installation **

 Now the klik client needs to be installed. This needs to be done only once.  Open a konsole and enter 
 wget klik.atekon.de/client/install -O - | sh
[IMG]http://img89.imageshack.us/img89/2676/kubuntu23vh.jpg[/IMG] 
**Depending on your system, you need to enter your password once during installation.** For most systems, this is your root password. For (K)Ubuntu, this is your (administrator) user password. (The password is needed only during the installation of the klik client and is not needed later when you get applications via klik.) 
 
** Firefox **

 If you want to use klik with Firefox, you need to open and close Firefox prior to the installation of the klik client. On systems without Firefox (such as Kubuntu), you can safely ignore this. 
[IMG]http://img89.imageshack.us/img89/5462/kubuntu36nm.jpg[/IMG] 
Some messages like these might occur, you can safely ignore them. 
[IMG]http://img137.imageshack.us/img137/7178/kubuntu47dh.jpg[/IMG] 
 
** Start using klik **

 Finally, the klik client is installed: 
[IMG]http://img85.imageshack.us/img85/884/kubuntu58ls.jpg[/IMG] 
If you had your Firefox browser open, **close it now** and re-open it in order make the klik:// protocol work. 
[IMG]http://img85.imageshack.us/img85/8049/kubuntu66fs.jpg[/IMG] 
Now navigate to [http://klik.atekon.de/](http://klik.atekon.de/) and start using klik. 
[IMG]http://img85.imageshack.us/img85/3558/kubuntu79yf.jpg[/IMG][http://klik.atekon.de/wiki/index.php/How_to_use_klik](http://klik.atekon.de/wiki/index.php/How_to_use_klik)

---

### Post by RAV TUX on 2007-01-27
continued from previous post:
> 
If you want to do a quick test, use klik://xvier - this is a very small "four in a row" game that runs on amost all systems. 
[IMG]http://img145.imageshack.us/img145/4990/kubuntu84bf.jpg[/IMG] 
Your software is now downloaded and run. 
[IMG]http://img85.imageshack.us/img85/8990/kubuntu92sc.jpg[/IMG] 
[IMG]http://img145.imageshack.us/img145/3268/kubuntu103pa.jpg[/IMG] 
After your software has run for the first time, you are asked about feedback for the klik download of this application. Please tell whether it worked, and if not please describe any error messages. This will help your fellow klik users to decide whether they want to download the software, and will help the klik developers to improve the service and fix failing application downloads. 
[IMG]http://img159.imageshack.us/img159/8926/kubuntu117db.jpg[/IMG][http://klik.atekon.de/wiki/index.php/How_to_use_klik](http://klik.atekon.de/wiki/index.php/How_to_use_klik)

---

### Post by RAV TUX on 2007-01-27
> [U][1 Design]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Design")
[/U]
  [U][1.1 How many files does a typical klik application install put onto my system?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_many_files_does_a_typical_klik_application_install_put_onto_my_system.3F")
[/U] 
 
 [U][2 Basics]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Basics")
[/U]
  [U][2.1 What do I need to use klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_do_I_need_to_use_klik.3F")
[2.2 Are there other requirements?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_other_requirements.3F")
[2.3 Which command should I use to prepare (K)Ubuntu for klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Which_command_should_I_use_to_prepare_.28K.29Ubuntu_for_klik.3F")
[2.4 Are there Linux distros which do not support cramfs by default?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_Linux_distros_which_do_not_support_cramfs_by_default.3F")
[2.5 Are there Linux distros which ship the klik client pre-installed?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_Linux_distros_which_ship_the_klik_client_pre-installed.3F")
[/U][QUOTE]Yes.  
 [LIST]
[*] [Kanotix]("http://www.kanotix.com/") (*[http://www.kanotix.com/](http://www.kanotix.com/)*) 2005-03 and newer,
[*] [SUSE SUPER SLICK]("http://www.opensuse.org/SLICK") (*[http://www.opensuse.org/SLICK](http://www.opensuse.org/SLICK)*),
[*] [CPX Mini]("http://www.informatik.hu-berlin.de/%7Ebading/cpx-mini/") (*[http://www.informatik.hu-berlin.de/~bading/cpx-mini/](http://www.informatik.hu-berlin.de/~bading/cpx-mini/)*),
[*] [RR4 Linux]("http://www.lxnaydesign.net/") (*[http://www.lxnaydesign.net/](http://www.lxnaydesign.net/)*) (Gentoo-based),[COLOR=Red]<<Now called Sabayon Linux>>[/COLOR] and
[*] [B2D Linux]("http://mrtg2.tnc.edu.tw/xoops") (*[http://mrtg2.tnc.edu.tw/xoops](http://mrtg2.tnc.edu.tw/xoops)*) (Taiwanese).[/LIST][http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_Linux_distros_which_ship_the_klik_client_pre-installed.3F](http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_Linux_distros_which_ship_the_klik_client_pre-installed.3F)
     
 
 [U][3 Installation]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Installation")
[/U]
  [U][3.1 How much effort is it to install the klik client on my system?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_much_effort_is_it_to_install_the_klik_client_on_my_system.3F")
[3.2 What is the procedure to install the klik client?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_is_the_procedure_to_install_the_klik_client.3F")
[3.3 What files does a klik client installation put into my system?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_files_does_a_klik_client_installation_put_into_my_system.3F")
[3.4 Does klik need root privileges to run its applications?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Does_klik_need_root_privileges_to_run_its_applications.3F")
[3.5 But I *did* come across this klik-ed application that asked me for the root password!! What gives?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#But_I_.2Adid.2A_come_across_this_klik-ed_application_that_asked_me_for_the_root_password.21.21_What_gives.3F")
[3.6 Is there an uninstall script for the klik client?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_an_uninstall_script_for_the_klik_client.3F")
[3.7 Is there an uninstall script for the klik-ed applications (the .cmg files)?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_an_uninstall_script_for_the_klik-ed_applications_.28the_.cmg_files.29.3F")
[/U]       
 
 [U][4 .cmg File Format]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#.cmg_File_Format")
[/U]
  [U][4.1 What is the file format of the klik applications?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_is_the_file_format_of_the_klik_applications.3F")
[4.2 Which type of files does the .cmg image include?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Which_type_of_files_does_the_.cmg_image_include.3F")
[4.3 What does the .cmg extension stand for?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_does_the_.cmg_extension_stand_for.3F")
[4.4 How can I make .cmg files executable on the command line?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_can_I_make_.cmg_files_executable_on_the_command_line.3F")
[4.5 can my changes to the apps saved back into cmg?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#can_my_changes_to_the_apps_saved_back_into_cmg.3F")
[4.6 can i combine multiple apps into one cmg with a launcher menu?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#can_i_combine_multiple_apps_into_one_cmg_with_a_launcher_menu.3F")
[/U]      
 
 [U][5 Scope]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Scope")
[/U]
  [U][5.1 What does the word "klik" stand for?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_does_the_word_.22klik.22_stand_for.3F")
[5.2 Does klik only work for KDE?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Does_klik_only_work_for_KDE.3F")
[5.3 Does klik only work for Knoppix and Kanotix?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Does_klik_only_work_for_Knoppix_and_Kanotix.3F")
[5.4 Do klik applications work for Redhat, Fedora, Mandriva and Slackware too?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Do_klik_applications_work_for_Redhat.2C_Fedora.2C_Mandriva_and_Slackware_too.3F")
[5.5 Can you make klik to fully support Redhat, Fedora, Mandriva and Slackware too?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_make_klik_to_fully_support_Redhat.2C_Fedora.2C_Mandriva_and_Slackware_too.3F")
[5.6 Is there a way to use klik without a browser, just from the command line?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_way_to_use_klik_without_a_browser.2C_just_from_the_command_line.3F")
[5.7 How do I use the klik client from the command line?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_do_I_use_the_klik_client_from_the_command_line.3F")
[5.8 Are there more browsers supporting klik:// type of links, apart from Konqueror?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_more_browsers_supporting_klik:.2F.2F_type_of_links.2C_apart_from_Konqueror.3F")
[/U][5.9 How do I make klik://appname links work for Mozilla?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_do_I_make_klik:.2F.2Fappname_links_work_for_Mozilla.3F")
[U] [5.10 How do I make klik://appname links work for Firefox?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_do_I_make_klik:.2F.2Fappname_links_work_for_Firefox.3F")
[5.11 How do I make klik://appname links work for Opera?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_do_I_make_klik:.2F.2Fappname_links_work_for_Opera.3F")
[5.12 How do I make klik://appname links work for elinks?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_do_I_make_klik:.2F.2Fappname_links_work_for_elinks.3F")
[5.13 I try to install xvier by following a klik://xvier link via the elinks browser that runs from a Linux console. I get [FIXME]]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#I_try_to_install_xvier_by_following_a_klik:.2F.2Fxvier_link_via_the_elinks_browser_that_runs_from_a_Linux_console._I_get__.5BFIXME.5D")
[/U]             
 
 [U][6 Usage]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Usage")
[/U]
  [U][6.1 Where does klik store the newly installed applications?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Where_does_klik_store_the_newly_installed_applications.3F")
[6.2 Why does it put all downloaded .cmgs onto the Desktop?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Why_does_it_put_all_downloaded_.cmgs_onto_the_Desktop.3F")
[6.3 Can I move the .cmg files away from my Desktop?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_I_move_the_.cmg_files_away_from_my_Desktop.3F")
[6.4 What do I need to do to install and run an application via klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_do_I_need_to_do_to_install_and_run_an_application_via_klik.3F")
[6.5 Is there a commandline client for klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_commandline_client_for_klik.3F")
[6.6 Can't you make the klik application more verbose?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can.27t_you_make_the_klik_application_more_verbose.3F")
[6.7 Why does it download xvier again and again each time I click on klik://xvier ?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Why_does_it_download_xvier_again_and_again_each_time_I_click_on_klik:.2F.2Fxvier_.3F")
[6.8 How can I run a klik application already present on my system?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_can_I_run_a_klik_application_already_present_on_my_system.3F")
[6.9 Can i run the klik-ed and locally saved application from the command line too (without re-download)?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_i_run_the_klik-ed_and_locally_saved_application_from_the_command_line_too_.28without_re-download.29.3F")
[6.10 I see most klik applications are for GUIs. Are there non-GUI ones too?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#I_see_most_klik_applications_are_for_GUIs._Are_there_non-GUI_ones_too.3F")
[6.11 What are the main use cases for klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_are_the_main_use_cases_for_klik.3F")
[6.12 Do you advise to leave the "old-school" package management systems like RPM or APT behind, and replace it with klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Do_you_advise_to_leave_the_.22old-school.22_package_management_systems_like_RPM_or_APT_behind.2C_and_replace_it_with_klik.3F")
[6.13 Can I use klik to run applications permanently?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_I_use_klik_to_run_applications_permanently.3F")
[6.14 Can I use klik to run applications from a USB stick?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_I_use_klik_to_run_applications_from_a_USB_stick.3F")
[6.15 Can I use klik to run applications from a CD?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_I_use_klik_to_run_applications_from_a_CD.3F")
[6.16 now that my klik apps moved into usb/cd, can i run it on any other distro?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#now_that_my_klik_apps_moved_into_usb.2Fcd.2C_can_i_run_it_on_any_other_distro.3F")
[6.17 Does klik work for GUI applications only?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Does_klik_work_for_GUI_applications_only.3F")
[6.18 Are there some "rules of thumb" for the type of applications that work with klik best?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_some_.22rules_of_thumb.22_for_the_type_of_applications_that_work_with_klik_best.3F")
[6.19 Can you tell which type of applications are not expected to work with klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_tell_which_type_of_applications_are_not_expected_to_work_with_klik.3F")
[6.20 Is it impossible to make the more complex applications work via klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_it_impossible_to_make_the_more_complex_applications_work_via_klik.3F")
[6.21 Is there a klik package for klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_klik_package_for_klik.3F")
[/U]                     
 
 [U][7 klik and the Base System]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#klik_and_the_Base_System")
[/U]
  [U][7.1 Will klik ever mess up my system library installations?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Will_klik_ever_mess_up_my_system_library_installations.3F")
[7.2 So you guarantee that running klik will not mess up with my local configuration?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#So_you_guarantee_that_running_klik_will_not_mess_up_with_my_local_configuration.3F")
[7.3 What can I do to safeguard my current config files from klik's interference?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_can_I_do_to_safeguard_my_current_config_files_from_klik.27s_interference.3F")
[/U]   
 
 [U][8 klik and Package Management]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#klik_and_Package_Management")
[/U]
  [U][8.1 Is klik a new alternative package management system?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_klik_a_new_alternative_package_management_system.3F")
[8.2 Is klik destined to become a package management system once it is more mature?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_klik_destined_to_become_a_package_management_system_once_it_is_more_mature.3F")
[8.3 If klik doesn't have a versioning and a package management of its own, how does it handle upgrades if there is f.e. discovered a vulnerability in Firefox?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#If_klik_doesn.27t_have_a_versioning_and_a_package_management_of_its_own.2C_how_does_it_handle_upgrades_if_there_is_f.e._discovered_a_vulnerability_in_Firefox.3F")
[8.4 What good is klik then for without decent versioning?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_good_is_klik_then_for_without_decent_versioning.3F")
[/U]    
 
 [U][9 Application Wishlist]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Application_Wishlist")
[/U]
  [U][9.1 Can I submit a new cool application for klik, so that there will be klik://coolapp link for it?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_I_submit_a_new_cool_application_for_klik.2C_so_that_there_will_be_klik:.2F.2Fcoolapp_link_for_it.3F")
[9.2 What exactly do you need for a new klik://coolapp to be accepted?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_exactly_do_you_need_for_a_new_klik:.2F.2Fcoolapp_to_be_accepted.3F")
[9.3 How is the list of package names available from the klik server created?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#How_is_the_list_of_package_names_available_from_the_klik_server_created.3F")
[/U]   
 
 [U][10 Troubleshooting]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Troubleshooting")
[/U]
  [U][10.1 I got a dialog saying "Error while trying to run xmule". What does this mean?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#I_got_a_dialog_saying_.22Error_while_trying_to_run_xmule.22._What_does_this_mean.3F")
[10.2 I get a message saying: "This package contains no application. klik can't handle it." -- What does this mean?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#I_get_a_message_saying:_.22This_package_contains_no_application._klik_can.27t_handle_it..22_--_What_does_this_mean.3F")
[10.3 Which package names are not feasible for klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Which_package_names_are_not_feasible_for_klik.3F")
[10.4 Why can't you remove those packages from the klik website which are not feasible for klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Why_can.27t_you_remove_those_packages_from_the_klik_website_which_are_not_feasible_for_klik.3F")
[10.5 I get a popup dialog telling me it is downloading a Debian package. But I am on SUSE, so I cancelled it! What gives??]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#I_get_a_popup_dialog_telling_me_it_is_downloading_a_Debian_package._But_I_am_on_SUSE.2C_so_I_cancelled_it.21_What_gives.3F.3F")
[10.6 I get a popup dialog telling me it is downloading multiple RPMs. But I am on Debian, so I cancelled it! What gives??]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#I_get_a_popup_dialog_telling_me_it_is_downloading_multiple_RPMs._But_I_am_on_Debian.2C_so_I_cancelled_it.21_What_gives.3F.3F")
[10.7 I read that klik uses a single file with a .cmg extension. Now I'm trying klik:/xyz and it pops up a dialog warning that it downloads a mixture of .debs, .rpms and .tgzs onto my sytem. No way! I cancelled the download. How do I get the single .cmg?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#I_read_that_klik_uses_a_single_file_with_a_.cmg_extension._Now_I.27m_trying_klik:.2Fxyz_and_it_pops_up_a_dialog_warning_that_it_downloads_a_mixture_of_.debs.2C_.rpms_and_.tgzs_onto_my_sytem._No_way.21_I_cancelled_the_download._How_do_I_get_the_single_.cmg.3F")
[10.8 Doesn't the mixture of ".debs, .rpms and .tgzs" lead to problems when executing the .cmg?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Doesn.27t_the_mixture_of_.22.debs.2C_.rpms_and_.tgzs.22_lead_to_problems_when_executing_the_.cmg.3F")
[10.9 Is there a very quick and minimum download method to test if the klik client installations works in principle?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_very_quick_and_minimum_download_method_to_test_if_the_klik_client_installations_works_in_principle.3F")
[10.10 Some klik applications do not terminate cleanly. I have some processes still running, and the mountpoint blocked. What can I do?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Some_klik_applications_do_not_terminate_cleanly._I_have_some_processes_still_running.2C_and_the_mountpoint_blocked._What_can_I_do.3F")
[/U]          
 
 [U][11 Tips+Tricks]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Tips.2BTricks")
[/U]
  [U][11.1 Is there a way to discover the exact recipe which is used to construct a given application via the klik://application link?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_way_to_discover_the_exact_recipe_which_is_used_to_construct_a_given_application_via_the_klik:.2F.2Fapplication_link.3F")
[11.2 Is there a way to re-construct the recipe that was used to construct a finished .cmg file?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_way_to_re-construct_the_recipe_that_was_used_to_construct_a_finished_.cmg_file.3F")
[11.3 Is there a way to force the usage of the Kanotix recipe for kitty, instead of the SUSE-10.0 one?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_way_to_force_the_usage_of_the_Kanotix_recipe_for_kitty.2C_instead_of_the_SUSE-10.0_one.3F")
[11.4 Can I enforce other variations of a klik recipe, if the standard one does not work for my system?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_I_enforce_other_variations_of_a_klik_recipe.2C_if_the_standard_one_does_not_work_for_my_system.3F")
[11.5 Is there a way to include the maximum number of dependencies into a given recipe, say the one for xvier?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_way_to_include_the_maximum_number_of_dependencies_into_a_given_recipe.2C_say_the_one_for_xvier.3F")
[11.6 What does "klik://xvier@scratch" do?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_does_.22klik:.2F.2Fxvier.40scratch.22_do.3F")
[11.7 What does "klik://xvier@multi" do?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_does_.22klik:.2F.2Fxvier.40multi.22_do.3F")
[11.8 What does "klik://xvier@kanotix0504" do?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_does_.22klik:.2F.2Fxvier.40kanotix0504.22_do.3F")
[11.9 What does "klik://xvier@breezy" do?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_does_.22klik:.2F.2Fxvier.40breezy.22_do.3F")
[/U]         
 
 [U][12 klik Recipe Maintainers]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#klik_Recipe_Maintainers")
[/U]
  [U][12.1 Who can become a klik recipe maintainer for, say, program "coolapp"?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Who_can_become_a_klik_recipe_maintainer_for.2C_say.2C_program_.22coolapp.22.3F")
[12.2 What is the advantage for a developer having his application in the klik database?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_is_the_advantage_for_a_developer_having_his_application_in_the_klik_database.3F")
[/U]  
 
 [U][13 Security]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Security")
[/U]
  [U][13.1 Isn't klik very unsafe? Why should I trust an arbitrary source to download a .cmg file from?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Isn.27t_klik_very_unsafe.3F_Why_should_I_trust_an_arbitrary_source_to_download_a_.cmg_file_from.3F")
[13.2 Can you show me a typical example of a recipe?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_show_me_a_typical_example_of_a_recipe.3F")
[13.3 What if I want to verify each step of the recipe before executing it?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_if_I_want_to_verify_each_step_of_the_recipe_before_executing_it.3F")
[13.4 What if I still do not trust klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#What_if_I_still_do_not_trust_klik.3F")
[13.5 Can't you introduce some sort of signing for your klik .cmg files, or for your recipes?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can.27t_you_introduce_some_sort_of_signing_for_your_klik_.cmg_files.2C_or_for_your_recipes.3F")
[13.6 Why should I trust the klik recipe maintainers?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Why_should_I_trust_the_klik_recipe_maintainers.3F")
[/U]      
 
 [U][14 Roadmap]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Roadmap")
[/U]
  [U][14.1 Can you make the directory configurable where klik stores my new .cmg files?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_make_the_directory_configurable_where_klik_stores_my_new_.cmg_files.3F")
[14.2 Can you make it so that the klik client reads a local .klikrc file to learn about my preferences?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_make_it_so_that_the_klik_client_reads_a_local_.klikrc_file_to_learn_about_my_preferences.3F")
[14.3 Can you make it so that each klik .cmg file has a unique icon associated to it, and not just the same standard one?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_make_it_so_that_each_klik_.cmg_file_has_a_unique_icon_associated_to_it.2C_and_not_just_the_same_standard_one.3F")
[14.4 Can you make it so that klik .cmg files are directly executable?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_make_it_so_that_klik_.cmg_files_are_directly_executable.3F")
[14.5 Can you utilize Plan9's 9P protocol (now supported in Linux Kernel 2.6.14) to enhance klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_utilize_Plan9.27s_9P_protocol_.28now_supported_in_Linux_Kernel_2.6.14.29_to_enhance_klik.3F")
[14.6 Can you create a more precise definition about what klik supposes to be a "Linux base system" for which all klik recipes would work?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_create_a_more_precise_definition_about_what_klik_supposes_to_be_a_.22Linux_base_system.22_for_which_all_klik_recipes_would_work.3F")
[14.7 Can you make it so that klik does not need /etc/fstab entries, but uses the new FUSE ("Filesystem in USrspacE") extension of the 2.6.14 Kernel?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Can_you_make_it_so_that_klik_does_not_need_.2Fetc.2Ffstab_entries.2C_but_uses_the_new_FUSE_.28.22Filesystem_in_USrspacE.22.29_extension_of_the_2.6.14_Kernel.3F")
[/U]       
 
 [U][15 Misc]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Misc")
[/U]
  [U][15.1 Who are the people behind klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Who_are_the_people_behind_klik.3F")
[/U] 
 
 [U][16 Support]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Support")
[/U]
  [U][16.1 Is there a klik online forum?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_klik_online_forum.3F")
[16.2 Is there a klik IRC channel?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_klik_IRC_channel.3F")
[16.3 Is there a klik mailing list?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Is_there_a_klik_mailing_list.3F")
[16.4 Where can I find more documentation about klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Where_can_I_find_more_documentation_about_klik.3F")
[/U]    
 
 [U][17 Supported Operating Systems]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Supported_Operating_Systems")
[/U]
  [U][17.1 Are there systems which ship ready to use with klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_systems_which_ship_ready_to_use_with_klik.3F")
[17.2 Are there systems which can be made to work with klik?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_systems_which_can_be_made_to_work_with_klik.3F")
[17.3 Are there systems which are unsupported or untested?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_systems_which_are_unsupported_or_untested.3F")
[17.4 Are there systems which are completely incompatible?]("http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Are_there_systems_which_are_completely_incompatible.3F")[/U][/quote][http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Design](http://klik.atekon.de/wiki/index.php/User%27s_FAQ#Design)

---

### Post by Tomosaur on 2007-01-27
Surely a link would have sufficed? :P

---

### Post by dvarsam on 2007-01-27
[QUOTE=Tomosaur]Dvarsam, please just give up. Your 'thing' has evolved from something which already exists, to something which doesn't do what you originally set out to do. I don't understand this part:

If the server and the client have identical stuff, then **what is the point**?[/quote]

You did NOT understand...
Please pay attention to what I am suggesting:

_You can have 2 ways to improve this_:

**Method 1**:
On the Clients side, when editing the "/etc/apt/sources.list" file, instead of adding the ..."deb [http://](http://)[color=blue]yourcache.example.com:3142/[/color]ftp.au.debian.org/debian unstable main contrib non-free"
... (above blue part) on _every_ single line in there...

Adding just a _single_ line **overall** like this:

deb [http://localhost:3142/apt-cacher](http://localhost:3142/apt-cacher)

All the rest of he lines can be removed/deleted or disabled!


**Method 2 (involves a GUI approach)**:
As said in my previous message, at the GUI I proposed in "Step 2" of my suggested implementation strategy:

Instead of: "[color=blue]Save all downloaded packages in the following folder
Location: /var/cache/apt/archives[/color]"

You could have: [color=blue]Use the following Repo instead of "/var/cache/apt/archives"
Repo: deb [http://localhost:3142/apt-cacher](http://localhost:3142/apt-cacher)[/color]

Note:
When you add the above line in the GUI, the Client PC's Repos are **disabled**!!!
The line "deb http://localhost:3142/apt-cacher" is doing the business/leading now...!!!
Outcome:
In this manner NO editing is performed on any Client's Repos (i.e. The Client's Repos & the Server's Repos have _identical_ contents) & the above line does all the work!!!
The User does NOT need to know (that by typing that line), the Client's Repos are disabled & the job is performed by that line which links/targets the Server's Repos...
_Advantages_:
In this manner you do NOT have to watch for typos in every single line of the Client PC's "/etc/apt/sources.list" file...
NOR do you have to maintain 2 Repo Files - 1 syntax for the Server & another syntax that applies to _every_ Network Client...

Admit it!
Now my idea is better than the current one!
I admit that I don't have the knowledge to know how things currently work, but with a little help, I can suggest some better ways of implementing things...
Besides, I want to make things easier for the users - I bet that everybody wants simpler solutions...!!!

[quote=Tomosaur]The existing solutions are **far easier, more efficient, and generally just better** than what you are proposing. All you need is a **server** and a bunch of **thin clients**.[/QUOTE]

The existing solutions can be improved!
Come on, accept it!

Thanks.

---

### Post by dvarsam on 2007-01-27
Dear user "RAV TUX",

Thanks for the link.
I think you did NOT understand what is the whole purpose of this...
The purpose is to _NOT_ having to download **Ubuntu Updates** on every Ubuntu Networked PC on an individual basis.
We want 1 Network PC to download all Ubuntu Updates & the rest of the Networked PCs be installing these upgraded from 1 Central Network Repository (which will be located on a single "Server" PC).

Example:
Lets say that the program "Totem" has bugs or vulnerabilities...
A Fix is created & is included on a package.
I perform an "**Ubuntu Update**" on my PC.
I am suggested to download & install a package that includes the code to fix the "Totem's" problem.
So that specific package might NOT be a full program!!!
It might just include some correcting code...

So your suggestion is "out of subject".
You are suggesting of a program/package that can help users run applications on their Ubuntu PCs without having to install them (in the first place)...

But some of the "**Ubuntu Update**" packages might NOT be programs at all!!!
So, where does your suggestion fit into this subject?

Thanks.

P.S.> If I have misunderstood this, please correct me...
BTW this is a nice program - I will keep this in mind/take a note of it! ;)

---

### Post by RAV TUX on 2007-01-27
> **dvarsam said:**
> Dear user "RAV TUX",

Thanks for the link.
I think you did NOT understand what is the whole purpose of this...
The purpose is to _NOT_ having to download **Ubuntu Updates** on every Ubuntu Networked PC on an individual basis.
We want 1 Network PC to download all Ubuntu Updates & the rest of the Networked PCs be installing these upgraded from 1 Central Network Repository (which will be located on a single "Server" PC).

Example:
Lets say that the program "Totem" has bugs or vulnerabilities...
A Fix is created & is included on a package.
I perform an "**Ubuntu Update**" on my PC.
I am suggested to download & install a package that includes the code to fix the "Totem's" problem.
So that specific package might NOT be a full program!!!
It might just include some correcting code...

So your suggestion is "out of subject".
You are suggesting of a program/package that can help users run applications on their Ubuntu PCs without having to install them (in the first place)...

But some of the "**Ubuntu Update**" packages might NOT be programs at all!!!
So, where does your suggestion fit into this subject?

Thanks.

P.S.> If I have misunderstood this, please correct me...
BTW this is a nice program - I will keep this in mind/take a note of it! ;)so...much like eBuilds in "emerge" on Gentoo/Sabayon?......where you can update by:

> emerge --syncthanks for the reply...and my apologies for not understanding the concept?

---

### Post by Tomosaur on 2007-01-27
> **dvarsam said:**
> You did NOT understand...
Please pay attention to what I am suggesting:

_You can have 2 ways to improve this_:

**Method 1**:
On the Clients side, when editing the "/etc/apt/sources.list" file, instead of adding the ..."deb [http://](http://)[color=blue]yourcache.example.com:3142/[/color]ftp.au.debian.org/debian unstable main contrib non-free"
... (above blue part) on _every_ single line in there...

Adding just a _single_ line **overall** like this:

deb [http://localhost:3142/apt-cacher](http://localhost:3142/apt-cacher)

All the rest of he lines can be removed/deleted or disabled!


**Method 2 (involves a GUI approach)**:
As said in my previous message, at the GUI I proposed in "Step 2" of my suggested implementation strategy:

Instead of: "[color=blue]Save all downloaded packages in the following folder
Location: /var/cache/apt/archives[/color]"

You could have: [color=blue]Use the following Repo instead of "/var/cache/apt/archives"
Repo: deb [http://localhost:3142/apt-cacher](http://localhost:3142/apt-cacher)[/color]

Note:
When you add the above line in the GUI, the Client PC's Repos are **disabled**!!!
The line "deb http://localhost:3142/apt-cacher" is doing the business/leading now...!!!
Outcome:
In this manner NO editing is performed on any Client's Repos (i.e. The Client's Repos & the Server's Repos have _identical_ contents) & the above line does all the work!!!
The User does NOT need to know (that by typing that line), the Client's Repos are disabled & the job is performed by that line which links/targets the Server's Repos...
_Advantages_:
In this manner you do NOT have to watch for typos in every single line of the Client PC's "/etc/apt/sources.list" file...
NOR do you have to maintain 2 Repo Files - 1 syntax for the Server & another syntax that applies to _every_ Network Client...

Admit it!
Now my idea is better than the current one!
I admit that I don't have the knowledge to know how things currently work, but with a little help, I can suggest some better ways of implementing things...
Besides, I want to make things easier for the users - I bet that everybody wants simpler solutions...!!!



The existing solutions can be improved!
Come on, accept it!

Thanks.

Listen - it's fairly obvious that you have no idea what you're asking for. When you say 'this is easier', you're not saying **anything**. Your method is 'easier' in the same way that telekenisis is easier than moving things by hand. Your perception of how things currently work is misguided and frankly, annoying. If you can't accept that **what you want is already there, in a better form**, then what do you expect people to say? "Oh yes, we'll get right on that!". You need to understand the principles behind what you're proposing, not just how you think it should work. Your method is one step forward and two steps backward. YES, things can always be 'easier' for the end user. YES, simplicity should be strived for. NO, your idea is not better. I will repeat, just to pound it into your skull once more:
**What you're proposing is already possible, in an easier, faster, and cleaner way**.

Your solution requires new code to be written - not only the frontend to apt, but the basic underlying system of how it works in the first place. Even if this was undertaken, you would still require the client machines to upgrade their software. This is still 'work', and seeing as you seem to want to avoid people ever actually using computers anyway, this is 'not good'.

NOW:

The existing method is very simple, and Ubuntu provides simple ways of achieving it:

1) You set up one computer, and connect it to the internet. This is the only computer which will ever upgrade its software.

2) You tell the client machines to connect to the server machine. When the user clicks, say Firefox from the menu, the client machine asks the server to send the Firefox program to the client. The user doesn't know this is happening, and everyone is happy. If Firefox is ever updated, then the SERVER machine upgrades firefox, and the user is not involved at all. Next time he opens Firefox, the server sends him the new version. Here, the client machine doesn't store any packages or software, it just requests them from the server machine as and when they are needed.

THIS IS FASTER, BETTER, AND MORE EFFICIENT.

So once again: your solution is a solution to a problem which doesn't exist. Stop trying to score brownie points by suggesting things which are pointless please.

---

### Post by Artemis3 on 2007-01-27
I have read this whole thread and, in my opinion, this is apt-proxy we are talking about.

apt-cacher seems trickier to use for new users, i don't understand why you choosed it, as it requires Apache and friends to be set up. Anyway the error described (localhost works but not 192.168.*.* sounds to me (don't take me seriously) that you need to tell apt-cacher somewhere what machines are allowed to connect to it. In this case your network is not allowed and only localhost (127.0.0.1) is. This is kind of a common practice in many daemon/servers when you first install them. Ah yes, reading your "user friendly" tutorial, look at this:

> you’ll probably want to take a look at a few configuration options such as allowed_hosts and denied_hosts. You can edit these settings in the /etc/apt-cacher/apt-cacher.conf

```
allowed_hosts=192.168.0.0/24 (to allow all local machines)

denied_hosts=
```

Have you missed this part? This means only allow access to machines beginning with 192.168.0. Yes, the first **three** numbers, _including the zero_.

In your examples you seem to have used the ip 192.168.**1**.2:3142 if you simply used the suggested config this will not work. You would need to edit the allowed_hosts line with either: 192.168.0.0/**16** or (better) 192.168.**1**.0/24.

The ip numbers are 4, and each represent 8 bits, going from 0 to 255. /24 is sort of like saying "omit the first 24 bits" meaning the first 3 numbers are fixed or n.n.n.*. /16 is only 2 numbers or n.n.*.* and /8 is n.*.*.*; You can use finer tune (/25, or /29) but lets not get complicated).

It's good that, because you used this harder method (instead of simply installing apt-proxy), you will end learning more than you wanted. In any event, using DNS is never required for any program as long as you don't mind manually assigning and remembering IP addresses for your own network. A little problem with "Zero config networks" is that you often need to find out what ip you have, and or what name was it given to your machine if there is a dns. This usually means 169.254/16 (remember what /16 means?)

So there; but i still think installing apt-proxy is much easier. You simply install it on a single machine and edit /etc/apt/sources.list in machines wanting to use the cache of that machine.

---

### Post by randell6564 on 2007-01-27
[FONT="Book Antiqua"][COLOR="Red"]**HUH!!!?**[/COLOR][/FONT]

---

### Post by koenn on 2007-01-28
> **Tomosaur said:**
> Surely a link would have sufficed? :P
Having to click a link is  not user-friendly. "People want simple things" :)

---

### Post by dvarsam on 2007-01-28
> **Artemis3I have read this whole thread and, in my opinion, this is apt-proxy we are talking about.
apt-cacher seems trickier to use for new users, i don't understand why you chosen it, as it requires Apache and friends to be set up.[/quote]

I have only tried "apt-cacher" because I had bumped into an easy HowTo.
That was all.
But unfortunately, setting this up turned into a nightmare... :(

[quote=Artermis3]Anyway the error described (localhost works but not 192.168.*.* sounds to me (don't take me seriously) that you need to tell apt-cacher somewhere what machines are allowed to connect to it. In this case your network is not allowed and only localhost (127.0.0.1) is. This is kind of a common practice in many daemon/servers when you first install them. Ah yes, reading your "user friendly" tutorial, look at this:

Have you missed this part? This means only allow access to machines beginning with 192.168.0. Yes, the first **three** numbers, _including the zero_.
In your examples you seem to have used the ip 192.168.**1**.2:3142 if you simply used the suggested config this will not work. You would need to edit the allowed_hosts line with either: 192.168.0.0/**16** or (better) 192.168.**1**.0/24....[/quote]

I have done the following:

1. nano /etc/apt-cacher/apt-cacher.conf
2. replaced "allowed_hosts=192.168.0.0/24" with "allowed_hosts=192.168.1.0/24"
3. /etc/init.d/apt-cacher restart

4. I then went on the Client side & from its menu, selected "System\Administration\Update Manager".
5. I clicked on the button named "Check" (to check for updates) & got this popup:

Title:Failure in receiving all the contents of the repository.

Message: The Repository might not be available any more or not be accessible due to networking problems. If there is  an older catalog version available to it, then this will be used. Otherwise the Repository will be ignored. Check your network connection and make sure the Repository is written correctly in preferences.

(Note: The Client is installed a localized version of Ubuntu - i.e. Greek & the above Message Text is "freely" translated - it might not look the same in an English Ubuntu install...)

Errors:
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) &#913 said:**
> http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-el.bz2:[/url] &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-el.bz2:](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:](http://127.0.0.1:3142/security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-el.bz2:](http://127.0.0.1:3142/security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-el.bz2:](http://127.0.0.1:3142/security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/Release.gpg:](http://127.0.0.1:3142/packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/i18n/Translation-el.bz2:](http://127.0.0.1:3142/packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/i18n/Translation-el.bz2:](http://127.0.0.1:3142/packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/si.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://127.0.0.1:3142/si.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/si.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-el.bz2:](http://127.0.0.1:3142/si.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/www.getautomatix.com/apt/dists/edgy/Release.gpg:](http://127.0.0.1:3142/www.getautomatix.com/apt/dists/edgy/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/deluge.mynimalistic.net/apt/dists/dapper/Release.gpg:](http://127.0.0.1:3142/deluge.mynimalistic.net/apt/dists/dapper/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/deluge.mynimalistic.net/apt/dists/dapper/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/deluge.mynimalistic.net/apt/dists/dapper/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/blognux.free.fr/debian/dists/unstable/Release.gpg:](http://127.0.0.1:3142/blognux.free.fr/debian/dists/unstable/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/blognux.free.fr/debian/dists/unstable/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/blognux.free.fr/debian/dists/unstable/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/flomertens.keo.in/ubuntu/dists/edgy/Release.gpg:](http://127.0.0.1:3142/flomertens.keo.in/ubuntu/dists/edgy/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/flomertens.keo.in/ubuntu/dists/edgy/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/flomertens.keo.in/ubuntu/dists/edgy/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/flomertens.keo.in/ubuntu/dists/edgy/main-all/i18n/Translation-el.bz2:](http://127.0.0.1:3142/flomertens.keo.in/ubuntu/dists/edgy/main-all/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/flomertens.keo.in/ubuntu/dists/edgy/testing/i18n/Translation-el.bz2:](http://127.0.0.1:3142/flomertens.keo.in/ubuntu/dists/edgy/testing/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/givre.cabspace.com/ubuntu/dists/edgy/Release.gpg:](http://127.0.0.1:3142/givre.cabspace.com/ubuntu/dists/edgy/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/givre.cabspace.com/ubuntu/dists/edgy/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/givre.cabspace.com/ubuntu/dists/edgy/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/givre.cabspace.com/ubuntu/dists/edgy/main-all/i18n/Translation-el.bz2:](http://127.0.0.1:3142/givre.cabspace.com/ubuntu/dists/edgy/main-all/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/givre.cabspace.com/ubuntu/dists/edgy/testing/i18n/Translation-el.bz2:](http://127.0.0.1:3142/givre.cabspace.com/ubuntu/dists/edgy/testing/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/extindt01.indt.org/VoIP/apt/dists/testing/Release.gpg:](http://127.0.0.1:3142/extindt01.indt.org/VoIP/apt/dists/testing/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/extindt01.indt.org/VoIP/apt/dists/testing/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/extindt01.indt.org/VoIP/apt/dists/testing/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/download.skype.com/linux/repos/debian/dists/stable/Release.gpg:](http://127.0.0.1:3142/download.skype.com/linux/repos/debian/dists/stable/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/download.skype.com/linux/repos/debian/dists/stable/non-free/i18n/Translation-el.bz2:](http://127.0.0.1:3142/download.skype.com/linux/repos/debian/dists/stable/non-free/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg:](http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-el.bz2:](http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-el.bz2:](http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-el.bz2:](http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
[http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-el.bz2:](http://127.0.0.1:3142/archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-el.bz2:) &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)

(Note: Wherever you bump into "&#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959;", it means "Impossible to connect to")

I then decided to go back and perform the following:

1. nano /etc/apt-cacher/apt-cacher.conf
2. replaced "allowed_hosts=192.168.1.0/24" with "allowed_hosts=*" (i.e. allow all - factory setting)
3. /etc/init.d/apt-cacher restart

But I still get the same Error!!! ](*,) 

[quote=Artemis3]It's good that, because you used this harder method (instead of simply installing apt-proxy), you will end learning more than you wanted. In any event, using DNS is never required for any program as long as you don't mind manually assigning and remembering IP addresses for your own network. A little problem with "Zero config networks" is that you often need to find out what ip you have, and or what name was it given to your machine if there is a dns. This usually means 169.254/16 (remember what /16 means?)

OK.

[quote=Artemis3]So there; but i still think installing apt-proxy is much easier. You simply install it on a single machine and edit /etc/apt/sources.list in machines wanting to use the cache of that machine.[/QUOTE]

OK, but "apt-cacher" works in a similar manner...
And something seems to be wrong on the Client's side - inside the file "/etc/apt/sources.list"...
But I can't seem to find what the problem is...
Any ideas?

Thanks.

---

### Post by dvarsam on 2007-01-28
[QUOTE=Tomosaur]Listen - it's fairly obvious that you have no idea what you're asking for. When you say 'this is easier', you're not saying **anything**. Your method is 'easier' in the same way that telekenisis is easier than moving things by hand. Your perception of how things currently work is misguided and frankly, annoying. If you can't accept that **what you want is already there, in a better form**, then what do you expect people to say? "Oh yes, we'll get right on that!". You need to understand the principles behind what you're proposing, not just how you think it should work.[/quote]

It is true, that I can NOT understand the principles involved...
I am NOT an OS mechanic, I am just a simple user...
And sure, IF I could understand how this thing worked & would have probably suggested a better solution or workaround.
I am suggesting things/improvements based on my current knowledge.
IF you personally know how things work, try to find a solution to this...

[quote=Tomosaur]Your method is one step forward and two steps backward. YES, things can always be 'easier' for the end user. YES, simplicity should be strived for. NO, your idea is not better. I will repeat, just to pound it into your skull once more:
**What you're proposing is already possible, in an easier, faster, and cleaner way**.[/quote]

How can it be considered "a cleaner way", when (on the Client) I have to edit/change/alter _every_ individual line in the "/etc/apt/sources.list" file...
... while I am proposing to edit/put/use _only_ a single line in there & let "apt-cacher" figure out the rest?
**Are you telling me that this is already possible?**
Then, show me how it is done...
Give me a link on this!

[quote=Tomosaur]Your solution requires new code to be written - not only the frontend to apt, but the basic underlying system of how it works in the first place. Even if this was undertaken, you would still require the client machines to upgrade their software. This is still 'work', and seeing as you seem to want to avoid people ever actually using computers anyway, this is 'not good'.[/quote]

You are implying that "apt-cacher" & "apt-proxy" do NOT require the user to update/upgrade their software...
But then, why am I selecting from the Client PC's menu "System\Administration\Update Manager" & then click on the button named "Check" (to check for updates) & get this popup:

Title:Failure in receiving all the contents of the repository.

If all updates/upgrades are done automatically on the Client's side, the above step would NOT be required would it?
How can I verify on the Client's side that your "sayings" are true?
a. I would need to find a package that needs to be updated...
b. Then check the current version.
c. Perform an update (or wait for the automatic one)
d. Verify whether the package has been updated.

How do you do that?
You do this from within Synaptic, by performing a "search"?
I can't think of any other way...

[quote=Tomosaur]NOW:
The existing method is very simple, and Ubuntu provides simple ways of achieving it:

1) You set up one computer, and connect it to the internet. This is the only computer which will ever upgrade its software.

2) You tell the client machines to connect to the server machine. When the user clicks, say Firefox from the menu, the client machine asks the server to send the Firefox program to the client. The user doesn't know this is happening, and everyone is happy. If Firefox is ever updated, then the SERVER machine upgrades firefox, and the user is not involved at all. Next time he opens Firefox, the server sends him the new version. Here, the client machine doesn't store any packages or software, it just requests them from the server machine as and when they are needed.[/quote]

Are you talking about the Server & some dummies involved again?
Cause this is the impression I have...
Sorry, but I don't have any dummies, my Ubuntu installations are currently a bunch of Ubuntu Desktops.
I don't know how the "Server & dummies" implementation works, but I am looking for a solution to solve things in my current Desktop implementation... 
Is there a solution for this implementation?

[quote=Tomosaur]THIS IS FASTER, BETTER, AND MORE EFFICIENT.
So once again: your solution is a solution to a problem which doesn't exist. Stop trying to score brownie points by suggesting things which are pointless please.[/QUOTE]

A faster, better, and more efficient solution would be to hire an Administrator do these things for me...
Also to hire a personal secretary to do the typing involved here...
A driver to drive me around in the city of Athens...
A chef to cook for me...
A trainer to help me keep my body fit...
And a massage-girl for the evenings... :)
...
...
... but since I can't afford all these & have to do things by myself, I am looking for an easy solution here...

Thanks.

P.S.> Please help!!!

---

### Post by shining on 2007-01-28
I was looking at avahi stuff, to know if I could do anything useful with it, and I felt on this :
[http://lists.debian.org/debian-devel/2006/11/msg00650.html](http://lists.debian.org/debian-devel/2006/11/msg00650.html)

---

### Post by dvarsam on 2007-01-28
[QUOTE=shining]I was looking at avahi stuff, to know if I could do anything useful with it, and I felt on this :
[http://lists.debian.org/debian-devel/2006/11/msg00650.html](http://lists.debian.org/debian-devel/2006/11/msg00650.html)[/QUOTE]

Very nice link you provided here!
IF you go & read the following part (which describes) how "apt-cacher" currently works:

> Concept
-------

When running more than one Debian box in a LAN with slow internet access
the most often used solution to prevent downloading the same Debian
package twice is running apt-cacher or the like on one single machine,
a centralized server.

The problem with this solution is, that every machine in the network
needs to be configured for this proxy. If it is down, no one can update.
If you go to another network, you must tweak your sources.list or
apt.conf in order to upgrade, which is quite common nowadays with
notebooks and wifi technology.

So, in my implementation:

1. The contents of "/etc/apt/sources.list" are the _same_ for every Networked PC (i.e. the Server & the Clients have exactly the same sources.list!!!)
2. On the new GUI I provided for Step 2 of my implementation, when you add that "Use the following Repo instead of /var/cache/apt/archives
Repo: deb http://localhost:3142/apt-cacher" part, you are disabling the Client's Repos & using the Server's Repos instead!
Now, IF you are given/offered the choice to disable that last line (maybe with a check box == disable the Server's Repo), in the case the Server is down, the Clients can use their own Repos to do the job (remember: the Client's Repos are _identical_ to Server's Repos!

As simple as that!!!
Why can't anybody understand what an improvement this is?

Thanks.

---

### Post by Tomosaur on 2007-01-28
> **dvarsam said:**
> It is true, that I can NOT understand the principles involved...
I am NOT an OS mechanic, I am just a simple user...
And sure, IF I could understand how this thing worked & would have probably suggested a better solution or workaround.
I am suggesting things/improvements based on my current knowledge.
IF you personally know how things work, try to find a solution to this...

Yes, you are just a user, and as such do not know what's involved. This does not make it easy, or even necessary, to implement what you're suggesting, because it is already there! I don't know how many times you need to be told this. No, it is not EXACTLY like your solution, but it IS THERE. Your solution requires extra time spent on adding these features - when there is a perfectly acceptable solution which does it all for you anyway.

> 
How can it be considered "a cleaner way", when (on the Client) I have to edit/change/alter _every_ individual line in the "/etc/apt/sources.list" file...
... while I am proposing to edit/put/use _only_ a single line in there & let "apt-cacher" figure out the rest?
**Are you telling me that this is already possible?**
Then, show me how it is done...
Give me a link on this!

What are you talking about? In the existing method, the clients never have to upgrade at all. At the very least, ALL you need to do is install a minimal Ubuntu installation for the client, and then connect to the X server on the server machine. This is slightly slower than doing it 'properly', which requires a bootable network card - which not everybody has, but it IS already there, and requires much less work than what you're suggesting. A 'real' thin client overview is [here](https://help.ubuntu.com/community/ThinClientHowto), but it is not necessarily as 'difficult' as the method outlined there.

The problem with your solution, which you seem to be conveniently overlooking - is that it doesn't **actually** solve any problems. Your solution still requires an internet connection - and it still requires more setting up than you seem to be aware of. You would NOT need to edit every single line with apt-cacher or apt-proxy or whatever, you could just use some very basic and logical method, and here it is. Open a terminal and type:
```

sudo echo "<whatever the new repo is>" > /etc/apt/sources.list

```
Hey presto, "every line" is altered. In case you don't quite understand that, it replaces the sources.list file with whatever line you want. "Oh no, you have to touch the command line!". Well no, you don't, because this could easily be made part of the installation procedure for apt-proxy, meaning your 'solution' is absolutely pointless, because it requires far more messing around than you're suggesting.

> 
You are implying that "apt-cacher" & "apt-proxy" do NOT require the user to update/upgrade their software...
But then, why am I selecting from the Client PC's menu "System\Administration\Update Manager" & then click on the button named "Check" (to check for updates) & get this popup:

Title:Failure in receiving all the contents of the repository.

If all updates/upgrades are done automatically on the Client's side, the above step would NOT be required would it?
How can I verify on the Client's side that your "sayings" are true?
a. I would need to find a package that needs to be updated...
b. Then check the current version.
c. Perform an update (or wait for the automatic one)
d. Verify whether the package has been updated.

How do you do that?
You do this from within Synaptic, by performing a "search"?
I can't think of any other way...

I would suggest it's because you have no idea what you're doing. If you don't even know how it currently works, how can you suggest improvements? What we've been saying, time and time again, is that your solution is unnecessary, because there is no problem to begin with. Your suggestions will just make more work for developers, which people will probably miss anyway because **what you're suggesting already exists**. PLEASE - stop saying 'You don't understand', because I do. I've said it over and over, and I don't know what more anyone can say to convince you that this is a massive waste of time, and  complicates an issue which is not currently complicated. **You** are having trouble configuring the necessary tools, but people have been doing it happily for quite a while now. Your own experience is not necessarily indicative of the 'average user'. I don't know what I'm supposed to 'admit'. Your solution makes things more difficult than they currently are. I can understand perfectly well that in _your_ mind, just being able to say 'use this repository' is perfectly legitimate, but what you don't seem to be able to grasp is that configuring the actual server is more difficult than just saying 'send upgrades to computer X'. You STILL need to configure a network, you STILL need ensure it all works smoothly. It's no simple task, but tools like apt-cacher and apt-proxy do it all for you. I really don't know what else to say, you just seem adamant on ignoring everything we're telling you.

> 
Are you talking about the Server & some dummies involved again?
Cause this is the impression I have...
Sorry, but I don't have any dummies, my Ubuntu installations are currently a bunch of Ubuntu Desktops.
I don't know how the "Server & dummies" implementation works, but I am looking for a solution to solve things in my current Desktop implementation... 
Is there a solution for this implementation?

Yes I am talking about the server & thin client combo again, because this is how it works, and how it should work, and what it was designed for - to eliminate the need of updating each and every computer, and for allowing easy access to your software and data from whatever node you're currently sitting at. 

> 
A faster, better, and more efficient solution would be to hire an Administrator do these things for me...
Also to hire a personal secretary to do the typing involved here...
A driver to drive me around in the city of Athens...
A chef to cook for me...
A trainer to help me keep my body fit...
And a massage-girl for the evenings... :)
...
...
... but since I can't afford all these & have to do things by myself, I am looking for an easy solution here...

Thanks.

P.S.> Please help!!!

You don't need to hire anybody to do this - anybody capable of reading and typing can do it. If you aren't prepared to learn what you need to do to accomplish tasks, then why do you own a computer? If you want to upgrade software, the price you pay is telling the computer what to do and, in some cases, how to do it. They're not magical boxes of electricity, they are tools and entertainment centers. Stop trying to dismiss everything I say as complex and stupid, this is just how it's done, and it has worked, and will continue to work, for years and years to come. We are already capable of doing what you're suggesting, and your solution does not make it any easier.

Below are the current methods of doing what you're trying to do:
1) Use apt-cacher/apt-proxy. This requires a server machine. Any machine which serves files is known as a server. Your solution requires a server. There are many server apps available - and the reason you can't set one up yourself is because a server is a pretty complex system. You need to enforce strict security measures, you need to know how a server works, and you need to know how to get two machines to talk to each other in the first place. You will need a firewall to block connections from outside your own network, and, in your solution, you will need to update each computer manually. This is more work than is actually necessary, because:

2) Use a server/thin client network. The 'proper' way of doing this requires a bootable network card on the client machine, which not everybody owns. After that, it's pretty much clean sailing. You still need a server machine, but there is already software freely available to aid in setting up such a system. This is what I've been telling you about all along, and you continually ignore it or dismiss it. You only need to ever update the server machine. This can be implemented on any home network - even yours.

3) Use X forwarding. This requires an X server only. The client machine connects to the server machine's X display, and thus is able to run programs on the server machine, but the display shows up on the client machine. Again - in this case, only the server machine ever needs to be upgraded (except when X itself gets upgraded, which would thus require the client machine to be upgraded too). This requires some configuration to get working, as does anything you ever do on a computer, because they're not telepathic.

4) Use the already available Ubuntu repo DVDs. Not a perfect solution, since you won't get upgrades, but one which suits many people just fine.

5) Just get a better internet connection.


There are probably a dozen more ways - but these are the ones which spring immediately to mind. 

So, in conclusion, I will repeat once more - your solution solves a non-existant problem. If you don't know how to set up a server, then your own solution wouldn't be available to you, since you would **still need to set up a server machine**.

---

### Post by shining on 2007-01-28
> **dvarsam said:**
> 
As simple as that!!!
Why can't anybody understand what an improvement this is?

Thanks.

Because it's not one. It doesn't add anything over the current apt-cacher / apt-proxy solution.
You still need to set up a server. 
And there is no need to change anything in the gui, synaptic already provides an interface for editing the /etc/apt/sources.list file. 
You just need to add your apt cacher/proxy server here, and that's all.

---

### Post by dvarsam on 2007-01-28
[QUOTE=Tomosaur]...what you're suggesting, is already there!
No, it is not EXACTLY like your solution, but it IS THERE.
Your solution requires extra time spent on adding these features - when there is a perfectly acceptable solution which does it all for you anyway.[/quote]

OK.

[quote=Tomosaur]In the existing method, the clients never have to upgrade at all.[/quote]

Well, in your suggested scenario, it is because they have NO Hard Drive...
They have NO OS installed...
And their OS is pulled from the Server!!!

[quote=Tomosaur]At the very least, ALL you need to do is install a minimal Ubuntu installation for the client, and then connect to the X server on the server machine.
This is slightly slower than doing it 'properly', which requires a bootable network card - which not everybody has, but it IS already there, and requires much less work than what you're suggesting. A 'real' thin client overview is [here](https://help.ubuntu.com/community/ThinClientHowto), but it is not necessarily as 'difficult' as the method outlined there.[/quote]

According to the link you provided:
> In more technical terms, the thin client can either obtain a kernel from local storage, or load the kernel across the network.

So, you are saying that I have 2 options:

1. Install a minimal Ubuntu install for the Client & connect to the X server (of the Server machine), or
2. Use a bootable NIC (no Ubuntu OS is installed on the Client PCs).

So, both of the above suggested solutions are called "Thin Client".
And according to the link you have provided:
 
> ...Using these instructions, you will collect the Linux kernel from the server using a bootable network card. This way, the thin client needs no more storage than the boot rom built into a bootable network card.

So the link you have provided is a HowTo perform the above 2nd option (from what I understand)...
Is that right?

And how do I know whether my Mobos are equipped with Bootable NICs?
I currently own 1 ADSL Router & 2 Mobos, both of which are equipped with onboard NICs.
(1 of them is supposed to be the Server & the other the client...)

_Questions_:
1. Do both of the NICs have to be Bootable or does that apply to the Clients only?
2. How can I determine whether these NICs are Bootable or not?

[quote=Tomosaur]The problem with your solution, which you seem to be conveniently overlooking - is that it doesn't **actually** solve any problems. Your solution still requires an Internet connection - and it still requires more setting up than you seem to be aware of. [/quote]

Sorry, but your solution does NOT require any Internet connection?
How on earth is the Server going to get updated if it does not have any Internet connection?
From CDs?
Downloaded from what - a 3rd PC?

[quote=Tomosaur]In your solution, you would NOT need to edit every single line with apt-cacher or apt-proxy or whatever, you could just use some very basic and logical method, and here it is.
Open a terminal and type:
```

sudo echo "<whatever the new repo is>" > /etc/apt/sources.list

```
Hey presto, "every line" is altered. In case you don't quite understand that, it replaces the sources.list file with whatever line you want. "Oh no, you have to touch the command line!". Well no, you don't, because this could easily be made part of the installation procedure for apt-proxy, meaning your 'solution' is absolutely pointless, because it requires far more messing around than you're suggesting.[/quote]

Sorry, but in your implementation, IF I only have 1 OS installed only on the Server side & the Clients have NO OS installed, then there is NO need to use "apt-proxy" or "apt-cacher" at all!!!
It is only the Server that is installed an OS, why not update from Synaptic instead?
The installation of "apt-proxy" or "apt-cacher" on a Server connected to Bootable NIC equipped Clients is irrelevant...
Probably it would only matter if the Thin Clients were installed a "minimal installation" of Ubuntu!
But not in the case where NO OS is installed on them...

_Why your strategy does NOT work (for my personal NEEDS)_:
* I have 2 PCs (I am getting my third one probably withing the coming week)
* 1 of them is booted at either Windows or Ubuntu (depending on my needs)
* The other is installed only Ubuntu!

_Disadvantages_:
* IF I follow your suggestion & make PC1 function as an Ubuntu Server, and at the same time convert the PC2 to be an Ubuntu Thin Client, In order to boot the PC2, the PC1 needs to be running too!!!
Example:
Whenever my Girl wants to type in her PC (i.e. PC2), I am required to boot PC1 too!
Usually my Girl types stuff in her PC2 which is in _her_ room (& NOT in _my_ room - PC1 is located there...!!!).
And since I don't want my Girl messing with my PC (PC1 in my room), she can user her own PC (PC2 in her room).
I don't want to have to boot 2 PCs while the job requires using/typing on only 1 of them...
* IF I want (for any reason) to boot my PC (PC1 in my room) to Windows & at the same time my Girl wants to use/boot her PC (PC2 in her room) in Ubuntu & her Ubuntu is the Thin Client, ... forget it!!!
... her Ubuntu won't be functional because it requires the booting/use of PC1 (i.e. the Ubuntu Server - which is _my_ PC), and since I am using it (& have booted in Windows), until I free my PC & reboot it to be the Linux Server again, she won't be able to use her PC (PC2 in her room) at all!!!

So you call this a "better" solution?
Sorry man, but your solution "s*cks" (for my needs)...
No offense, but unless there is some alternative way on doing things, I don't want to mess with setting up something like this, as it is against my basic needs...!!!

I want my PCs to be flexible & independent from each other...
"Independence" is all that matters to me...
And your solution implies that PC2 is **dependent** on PC1 (the Server PC)!!!
**In your solution IF PC1 (Server) is NOT running, you can't run PC2 either!**
The solution you are providing is aiming/targeting Work/Business Environments but NOT designed for Home use...
Since I can't find program alternatives in the Ubuntu world, to be as good/equal compared to the ones I can find in the Windows world, then for NOW I will be dependent on both Operating  Systems...
When Ubuntu grows better & bigger, I might consider your suggestion as an option...
Currently your suggestion ain't for Home Users (that want Flexibility), but for Business users only!!!
Your solution is removing/taking away the "flexibility" I enjoy in my Home Network...
I want to be able to boot my machines:

1. PC1 (Ubuntu) < - > PC2 (Ubuntu)
2. PC1 (Ubuntu) < - > PC2 (Windows)
2. PC1 (Windows) < - > PC2 (Windows)

And I want each of the above PCs to be independent from each other!!!
I would accept co-dependence if that Included _only_ the Updating of OS (i.e. "apt-cacher" or "apt-proxy") - **not** a complete dependency (including Booting)...
I want to keep the Booting independent!!!

Again, your solution is "out of question" unless it includes "independence" in all aspects except OS updates... 

[quote= Tomosaur]I would suggest it's because you have no idea what you're doing. If you don't even know how it currently works, how can you suggest improvements? What we've been saying, time and time again, is that your solution is unnecessary, because there is no problem to begin with. Your suggestions will just make more work for developers, which people will probably miss anyway because **what you're suggesting already exists**. PLEASE - stop saying 'You don't understand', because I do. I've said it over and over, and I don't know what more anyone can say to convince you that this is a massive waste of time, and  complicates an issue which is not currently complicated. **You** are having trouble configuring the necessary tools, but people have been doing it happily for quite a while now. Your own experience is not necessarily indicative of the 'average user'. I don't know what I'm supposed to 'admit'. Your solution makes things more difficult than they currently are. I can understand perfectly well that in _your_ mind, just being able to say 'use this repository' is perfectly legitimate, but what you don't seem to be able to grasp is that configuring the actual server is more difficult than just saying 'send upgrades to computer X'. You STILL need to configure a network, you STILL need ensure it all works smoothly. It's no simple task, but...[/quote]

I might not know what I am doing, but one thing is for sure...
I do know, what I _want_ to do!!!
I do know, how I want my Ubuntu PCs to function...
And this is not negotiable...
My solution is necessary for _me_ (and hopefully for others too!).
This is a "waiste of time" for _you_, not for me...
Unless you have to provide a solution for _my_ needs, I am still backing up my original argument!

[quote=Tomosaur]...tools like apt-cacher and apt-proxy do it all for you. I really don't know what else to say, you just seem adamant on ignoring everything we're telling you.[/quote]

IF "apt-cacher" & "apt-proxy" do it all for me, then tell me how...
But I warn you, **IF** your solution is removing the flexibility I asked in the first place (i.e. being able to run any OS in any of the Networked PCs _independently_), then your solution is NOT a solution for me!!!

[quote=Tomosaur]Yes I am talking about the server & thin client combo again, because this is how it works, and how it should work, and what it was designed for - to eliminate the need of updating each and every computer, and for allowing easy access to your software and data from whatever node you're currently sitting at.[/quote]

...and also eliminates the possibility of being able to run Windows on 1 PC & Linux on the Other - especially when I want to run Windows on the PC1 (i.e. the Linux Server) & Linux on the PC2 (i.e. the Linux Thin Client).
The PC2 won't run because it is NOT capable of running by itself...
Wow, what a great solution of yours...
(IF I am wrong please correct me...)

[quote=Tomosaur]You don't need to hire anybody to do this - anybody capable of reading and typing can do it. If you aren't prepared to learn what you need to do to accomplish tasks, then why do you own a computer? If you want to upgrade software, the price you pay is telling the computer what to do and, in some cases, how to do it. They're not magical boxes of electricity, they are tools and entertainment centers. Stop trying to dismiss everything I say as complex and stupid, this is just how it's done, and it has worked, and will continue to work, for years and years to come. We are already capable of doing what you're suggesting, and your solution does not make it any easier.[/quote]

I am not trying to dismiss everything you say is "st*pid"...
For god's sake, I never said that!
I appreciate you are helping me man, I really do!!!
But for some reason I feel you don't understand my true "needs"...
You are trying to convince me to adopt a Server-Dummy Client environment which "by default" is removing all the "flexibility" I truly need...
IF there is some other solution for this, please share with me...
But don't try to convince me that things already exist, while they don't...
I would love to implement the Server-Dummy Client scenario, but only for experimental purposes...

[quote=Tomosaur]Below are the current methods of doing what you're trying to do:
1) Use apt-cacher/apt-proxy. This requires a server machine. Any machine which serves files is known as a server. Your solution requires a server. There are many server apps available - and the reason you can't set one up yourself is because a server is a pretty complex system. You need to enforce strict security measures, you need to know how a server works, and you need to know how to get two machines to talk to each other in the first place. You will need a firewall to block connections from outside your own network, and, in your solution, you will need to update each computer manually.[/quote]

I currently have installed Ubuntu Desktop on 2 PCs - i.e. PC1 & PC2.
As you said above, "Any machine which serves files is known as a server."
So, I can basically turn/transform 1 of my Desktops to being a Server...
I have already transformed my PC1 to being a Web Server...
(Installed apache, mysql, php...)
I also have a Router & have opened up Port 80 for incoming traffic.
I know how to set up Static IPs on the Networked PCs.
I have installed "apt-cacher" but can't make it work on the PC2.
When I ask PC2 to update, I get errors...
**IF** PC2 is required to be a Dummy Client & NOT a Desktop Client, maybe then, that is the reason why things don't work...
I have managed to making SSH connections.
I have managed to making NFS connections (unfortunately only 1-way).
For a Firewall I have the US Robotics ADSL Router.
What else is there to know...?

In my solution, I want 2 Ubuntu PC Desktops to share a single Repository for Ubuntu Updates.
That is all...
As simple as that...
No Server-Dummy Clients...
No complicated stuff...
Something really easy...
1+1=2
And that was what I thought "apt-cacher" or "apt-proxy" were designed for, in the first place...
Am I right or wrong here?
Can "apt-cacher" or "apt-proxy" work on 2 Networked Ubuntu Desktop Installs?
Or do I have to Format one of the Hard Drives & install something else (like a Thin Client)?

[quote=Tomosaur]This is more work than is actually necessary, because:

2) Use a server/thin client network. The 'proper' way of doing this requires a bootable network card on the client machine, which not everybody owns. After that, it's pretty much clean sailing. You still need a server machine, but there is already software freely available to aid in setting up such a system. This is what I've been telling you about all along, and you continually ignore it or dismiss it. You only need to ever update the server machine. This can be implemented on any home network - even yours.[/quote]

Yes, but there is always some "constraints" involved...
Like the one I mentioned:
"You can't run Windows on the Server side & expect the Ubuntu Thin Client to be able to boot solo"...
At the same time "apt-cacher" & "apt-proxy" are irrelevant if a Server is the only PC that contains an OS installed...
The Client PCs contain no OS, so there is nothing to update really...

[quote=Tomosaur]3) Use X forwarding. This requires an X server only. The client machine connects to the server machine's X display, and thus is able to run programs on the server machine, but the display shows up on the client machine. Again - in this case, only the server machine ever needs to be upgraded (except when X itself gets upgraded, which would thus require the client machine to be upgraded too). This requires some configuration to get working, as does anything you ever do on a computer, because they're not telepathic.

4) Use the already available Ubuntu repo DVDs. Not a perfect solution, since you won't get upgrades, but one which suits many people just fine.

5) Just get a better Internet connection.


There are probably a dozen more ways - but these are the ones which spring immediately to mind. 

So, in conclusion, I will repeat once more - your solution solves a non-existant problem. If you don't know how to set up a server, then your own solution wouldn't be available to you, since you would **still need to set up a server machine**.[/QUOTE]

From the above solutions you provided, I can see the solutions 1-3 to be more appropriate in General...
For _my_ specific needs, I see only solution 1 to be appropriate...
I need to make 1 of my 2 Ubuntu Desktops to act as a Repo Server...
All other jobs are performed independently from each Networked PC...

The solution 3 (you mentioned above) sounds like solution 2, I can't see the difference between them...
Is the PC2 installed a Desktop install, and only the X of the PC1 is shared?

Hopefully with what I have clarified we are getting into somewhere...
I truly hope so...

Thanks.

---

### Post by ssam on 2007-01-28
i just stubled across this
[http://trac.phidev.org/trac/wiki/AptZeroconf](http://trac.phidev.org/trac/wiki/AptZeroconf)

> When running more than one Debian box in a LAN with slow internet access the most often used solution to prevent downloading the same Debian package twice is running apt-cacher or the like on one single machine, a centralized server.

The problem with this solution is, that every machine in the network needs to be configured for this proxy. If it is down, no one can update. If you go to another network, you must tweak your sources.list or apt.conf in order to upgrade, which is quite common nowadays with notebooks and wifi technology.

We would therefore be interested in an automatic and peer-to-peer solution. When there is no apt caching daemon in the LAN, we want to fetch the packages directly from the internet. But if there is one or even more available, apt should automatically use it, without any configuration from the user. This is by the way the reason we called it apt-zeroconf in the first place.

The next question is: Who runs an apt caching daemon? In our first implementation, everyone running apt-zeroconf also shares his apt package cache in /var/cache/apt/archives to everyone in the network.

Now, one might think this could potentially pose a security threat as everyone can offer and distribute debs without any authentication whatsoever. This is not the case as we are not yet caching the package lists or pdiffs, which are PGP-signed and contain MD5, SHA1 and SHA256 checksums of the packages. But due to the trusted PGP signatures, caching package lists shouldn't be an issue. 

---

### Post by dvarsam on 2007-01-28
Hello again!

In all your replying posts, you have been suggesting me to tryout "apt-proxy" instead of "apt-cacher"...

And so I did!
1.I uninstalled "apt-cacher".
2. I installed "apt-proxy"
3. Followed this HowTo: [https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)
4. Edited the file "/etc/apt-proxy/apt-proxy-v2.conf"
    (BTW this syntax is more complex compared to that of "apt-cacher"...)
5. Added all the Repos involved in the appropriate syntax.
6. Restarted "apt-proxy"
7. Imported into "apt-proxy" the Ubuntu's Repos from folder "/var/cache/apt/archives"
8. Edited the "/etc/apt/sources.list" on the Client PC.
9. On the Client PC, from the Menu I selected "System\Administration\Update Manager".
10. I got the same Error I was getting when using the program "apt-cacher"!!!

Outcome:
NO Ubuntu Updates can be installed on the Client PCs...
How awesome... :)

So, what do I do?
Any suggestions?

Thanks

---

### Post by koenn on 2007-01-29
> 10. I got the same Error I was getting when using the program "apt-cacher"!!!
Exactly what error was that again ? 

BTW have you seen the apt zeroconf links. Looks fun too.

---

### Post by dvarsam on 2007-01-29
Hello & thanks for your reply!

[QUOTE=koenn]Exactly what error was that again ?[/quote]

The same Error as stated in **Page 6** of this Thread & **3rd "dvarsam's" Post** (created by me)...

[quote=koenn]BTW have you seen the apt zeroconf links. Looks fun too.[/QUOTE]

You mean: installing/trying out another program?
Something diff to "apt-cacher" & "apt-proxy"?
Shouldn't I first exhaust the possibility of making these work & then tryout a diff package/program?

Thanks.

P.S.> If worse comes to worse, just "shoot out" what you want me to do...
I am open up for anything at the moment...
(including the option of taking a hammer & turning my PC into powder... lol)

---

### Post by koenn on 2007-01-29
you mean this one ?
```

http://127.0.0.1:3142/gr.archive.ubu...y/Release.gpg: &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
http://127.0.0.1:3142/gr.archive.ubu...lation-el.bz2: &#913;&#948;&#973;&#957;&#945;&#964;&#951; &#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; &#963;&#964;&#959; 127.0.0.1:3142 (127.0.0.1). - connect (111 Connection refused)
```

That doesn't make sense at all, do you have a sources.list (synaptic / software properties media list) that has entries like 
```
deb http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/ edgy
```
or something equally meaningless ?

---

### Post by dvarsam on 2007-01-29
> **koenn]you mean this one ?
```

http://127.0.0.1:3142/gr.archive.ubu...y/Release.gpg: &#913 said:**
> 

Yes, this is what I meant...

[quote=koenn]That doesn't make sense at all, do you have a sources.list (synaptic / software properties media list) that has entries like 
```
deb http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/ edgy
```
or something equally meaningless ?

Here is my "**apt-proxy-2.conf**" file contents:

```

[DEFAULT]
;; All times are in seconds, but you can add a suffix
;; for minutes(m), hours(h) or days(d)

;; Server IP to listen on

;address = 192.168.0.254

;; Server port to listen on

port = 9999

;; Control files (Packages/Sources/Contents) refresh rate
;;
;; Minimum time between attempts to refresh a file

min_refresh_delay = 1s

;; Minimum age of a file before attempting an update (NOT YET IMPLEMENTED)

;min_age = 23h

;; Uncomment to make apt-proxy continue downloading even if all
;; clients disconnect.  This is probably not a good idea on a
;; dial up line.
;; complete_clientless_downloads = 1

;; Debugging settings.
;; for all debug information use this:
;; debug = all:9

debug = all:4 db:0

;; Debugging remote python console
;; Do not enable in an untrusted environment

;telnet_port = 9998
;telnet_user = apt-proxy
;telnet_password = secret

;; Network timeout when retrieving from backend servers

timeout = 15

;; Cache directory for apt-proxy

cache_dir = /var/cache/apt-proxy

;; Use passive FTP? (default=on)

;passive_ftp = on

;; Use HTTP proxy?

;http_proxy = host:port

;; Limit download rate from backend servers (http and rsync only), in bytes/sec

;bandwidth_limit = 100000

;; Enable HTTP pipelining within apt-proxy (for test purposes)

;disable_pipelining=0

;;--------------------------------------------------------------
;; Cache housekeeping

;; Time to perform periodic housekeeping:
;;  - delete files that have not been accessed in max_age
;;  - scan cache directories and update internal tables

cleanup_freq = 1d

;; Maximum age of files before deletion from the cache (seconds)

max_age = 120d

;; Maximum number of versions of a .deb to keep per distribution

max_versions = 3

;; Add HTTP backends dynamicaly if not already defined? (default=on)

;dynamic_backends = on

;;---------------------------------------------------------------
;;---------------------------------------------------------------
;; Backend servers
;;
;; Place each server in its own [section]

;; For Ubuntu v6.10 - Edgy Eft:
;; ---------------------------

[debian]
;; The main Debian archive
;; You can override the default timeout like this:

;timeout = 30

;; Rsync server used to rsync the Packages file (NOT YET IMPLEMENTED)
;;rsyncpackages = rsync://ftp.de.debian.org/debian

;; Backend servers, in order of preference

backends = 
	[http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian)
	[http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian)
	[http://ftp2.de.debian.org/debian](http://ftp2.de.debian.org/debian)
	[ftp://ftp.uk.debian.org/debian](ftp://ftp.uk.debian.org/debian)

[security]
;; Debian security archive

backends = 
	[http://security.debian.org/debian-security](http://security.debian.org/debian-security)
	[http://ftp2.de.debian.org/debian-security](http://ftp2.de.debian.org/debian-security)

[ubuntu]
;; Ubuntu archive

backends = [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

[ubuntu-security]
;; Ubuntu security updates

backends = [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

;[openoffice]
;; OpenOffice.org packages

;backends =
;	[http://ftp.freenet.de/pub/debian-openoffice](http://ftp.freenet.de/pub/debian-openoffice)
;	[http://ftp.sh.cvut.cz/MIRRORS/OpenOffice.deb](http://ftp.sh.cvut.cz/MIRRORS/OpenOffice.deb)
;	[http://borft.student.utwente.nl/debian](http://borft.student.utwente.nl/debian)
	
;[apt-proxy]
;; Apt-proxy new versions

;backends = [http://apt-proxy.sourceforge.net/apt-proxy](http://apt-proxy.sourceforge.net/apt-proxy)

;[backports.org]
;; backports.org

;backends = [http://backports.org/debian](http://backports.org/debian)

;[blackdown]
;; Blackdown Java

;backends = [http://ftp.gwdg.de/pub/languages/java/linux/debian](http://ftp.gwdg.de/pub/languages/java/linux/debian)


;[debian-people]
;; people.debian.org

;backends = [http://people.debian.org](http://people.debian.org)

;[emdebian]
;; The Emdebian project

;backends = [http://emdebian.sourceforge.net/emdebian](http://emdebian.sourceforge.net/emdebian)

;[rsync]
;; An example using an rsync server.  This is not recommended
;; unless http is not available, becuause rsync is only more
;; efficient for transferring uncompressed files and puts much
;; more overhead on the server.  See the rsyncpacakges parameter 
;; for a way of rsyncing just the Packages files.

;backends = rsync://ftp.uk.debian.org/debian

;; --------------------------------------------------------------
;; --------------------------------------------------------------

[Default]
;; These were included by default on a newly installed Ubuntu v6.10 OS:

backends =
	[http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu)
;	[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)    ( < - Already mentioned above)
	[http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu)
	[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)


;; --- 01. ---
[w32 codecs]
backends =
	[http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf)

;; --- 02. ---
[mplayer-386]
backends =
	[http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu)

;; --- 03. ---
[automatix]
backends =
	[http://www.getautomatix.com/apt](http://www.getautomatix.com/apt)

;; --- 04. ---
[deluge]
backends =
	[http://deluge.mynimalistic.net/apt](http://deluge.mynimalistic.net/apt)

;; --- 05. ---
[easycam2]
backends =
	[http://blognux.free.fr/debian](http://blognux.free.fr/debian)

;; --- 06. ---
[ntfs-3g]
backends =
	[http://flomertens.keo.in/ubuntu](http://flomertens.keo.in/ubuntu)
	[http://givre.cabspace.com/ubuntu](http://givre.cabspace.com/ubuntu)


;; --- 07. ---
[tapioca]
backends =
	[http://extindt01.indt.org/VoIP/apt](http://extindt01.indt.org/VoIP/apt)

;; --- 08. ---
[frostwire]
backends =
	[http://peercommons.com/frostwire/4.13.1](http://peercommons.com/frostwire/4.13.1)

;; --- 09. ---
[skype]
backends =
	[http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian)

;; --- 10. ---
[backports]
backends =
	[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports
```

And here are the contents of the Client PC's "**/etc/apt/sources.list**" file:

```
# For Ubuntu v6.10 - Edgy Eft:
# ---------------------------

deb [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/) edgy-updates main restricted


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/) edgy universe


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://127.0.0.1:9999/security.ubuntu.com/ubuntu](http://127.0.0.1:9999/security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://127.0.0.1:9999/security.ubuntu.com/ubuntu](http://127.0.0.1:9999/security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://127.0.0.1:9999/security.ubuntu.com/ubuntu](http://127.0.0.1:9999/security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://127.0.0.1:9999/security.ubuntu.com/ubuntu](http://127.0.0.1:9999/security.ubuntu.com/ubuntu) edgy-security universe


## This was added (as asked)
## Multiverse

deb [http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu](http://127.0.0.1:9999/gr.archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://127.0.0.1:9999/archive.ubuntu.com/ubuntu](http://127.0.0.1:9999/archive.ubuntu.com/ubuntu) edgy multiverse

# ------------------------------------------------------------------------

## --- 01. ---
## The following 2 lines are required for the "w32codecs" package:

deb [http://127.0.0.1:9999/packages.freecontrib.org/ubuntu/plf/](http://127.0.0.1:9999/packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free
deb-src [http://127.0.0.1:9999/packages.freecontrib.org/ubuntu/plf/](http://127.0.0.1:9999/packages.freecontrib.org/ubuntu/plf/) edgy-plf free non-free

## When finished, on a Terminal window, type the following:
##
## wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
##
## Note: The above way, is a manual way to add the Public Key to provide
##       access to the "w32codecs" code database.

## --- 02. ---
## This line is required if you want to be able to install the "mplayer-386"
## package:
## Note: Even though I added the line, I can't seem to find the package.

deb [http://127.0.0.1:9999/si.archive.ubuntu.com/ubuntu](http://127.0.0.1:9999/si.archive.ubuntu.com/ubuntu) edgy multiverse

## --- 03. ---
## This line is required if you want to be able to install "automatix":

deb [http://127.0.0.1:9999/www.getautomatix.com/apt](http://127.0.0.1:9999/www.getautomatix.com/apt) edgy main

## When finished, on a Terminal window, type the following:
##
## wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
## gpg --import key.gpg.asc
## gpg --export --armor 521A9C7C | sudo apt-key add -
##
## Note: The above way, is a manual way to add the Public Key to provide
##       access to the "automatix" code database.

## --- 04. ---
## This is required if you would like to install package "deluge",
## a bittorrent client (used for downloads):

deb [http://127.0.0.1:9999/deluge.mynimalistic.net/apt](http://127.0.0.1:9999/deluge.mynimalistic.net/apt) dapper main

## --- 05. ---
## This is required if you would like to install a Webcam.
## The Repo below, helps you locate & install the required package 
## named "easycam2".

deb [http://127.0.0.1:9999/blognux.free.fr/debian](http://127.0.0.1:9999/blognux.free.fr/debian) unstable main

## --- 06. ---
## This is required if you would like to install "ntfs-3g" latest edition:

# deb [http://127.0.0.1:9999/givre.cabspace.com/ubuntu/](http://127.0.0.1:9999/givre.cabspace.com/ubuntu/) edgy main-all
# deb [http://127.0.0.1:9999/ntfs-3g.sitesweetsite.info/ubuntu/](http://127.0.0.1:9999/ntfs-3g.sitesweetsite.info/ubuntu/) edgy main-all
# deb [http://127.0.0.1:9999/flomertens.keo.in/ubuntu/](http://127.0.0.1:9999/flomertens.keo.in/ubuntu/) edgy main-all

deb [http://127.0.0.1:9999/flomertens.keo.in/ubuntu](http://127.0.0.1:9999/flomertens.keo.in/ubuntu) edgy main main-all testing
deb [http://127.0.0.1:9999/givre.cabspace.com/ubuntu](http://127.0.0.1:9999/givre.cabspace.com/ubuntu) edgy main main-all testing

## --- 07. ---
## This is required if you would like to install "tapioca" latest edition:

deb [http://127.0.0.1:9999/extindt01.indt.org/VoIP/apt](http://127.0.0.1:9999/extindt01.indt.org/VoIP/apt) testing main

## --- 08. ---
## This is required if you would like to install "frostwire" latest edition:

# deb [http://127.0.0.1:9999/peercommons.com/frostwire/4.13.1/](http://127.0.0.1:9999/peercommons.com/frostwire/4.13.1/)

## --- 09. ---
## This is required if you would like to install "skype" latest edition:

deb [http://127.0.0.1:9999/download.skype.com/linux/repos/debian/](http://127.0.0.1:9999/download.skype.com/linux/repos/debian/) stable non-free

## --- 10. ---
## Backports:

deb [http://127.0.0.1:9999/archive.ubuntu.com/ubuntu](http://127.0.0.1:9999/archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
```

Of course, the same "/etc/apt/sources.list" apply to the Server PC too!
Only, in the Server's Repos, the part you see above - i.e. "127.0.0.1:9999/" - must be removed from every line, so that the Repo can be applied to the Server PC!
So, the Sources.list of the Server, work fine! & the Server updates correctly!
But the Client does NOT!!!
It creates the Errors you seem to "find" not making sense...

Thanks.

---

### Post by koenn on 2007-01-30
> It creates the Errors you seem to "find" not making sense...
It's not the errors that i find 'not making sense'. It's the content of your sources.list (that i deduced from the errors and that turn out +/- as i expected) that i find meaningless. You acually qouted that part in your reply. Read it again

On first sight the config file for apt-proxy looks ok. I didn't look closely; but its probably the default that came with the package ? 
Do remove that " ( < - Already mentioned above)" thing - it will ruin the file

As said before, the statements in your sources.list are meaningless. 
replace the sources.list on one of the clients with this :

```
deb http://your.server.ip.address:9999/Default/ edgy main restricted universe 
deb http://your.server.ip.address:9999/Default/ edgy-updates main restricted
deb http://your.server.ip.address:9999/Default/ edgy-backports main restricted universe 
deb http://your.server.ip.address:9999/Default/ edgy-security main restricted universe

```

make sure you use the correct ip address in stead of your.server.ip.address. 
The correct ip address is NOT 127.0.0.1

see if it works.

---

### Post by dvarsam on 2007-01-30
> **koenn]...I don't find the content of your sources.list making sense...
You actually quoted that part in your reply. Read it again[/quote]

Which specific part are you talking about?

[quote=koenn]On first sight the config file for apt-proxy looks ok.
I didn't look closely said:**
> 

But if you take a clear look on the file "**apt-proxy-2.conf**", that line is disabled:

[quote=dvarsam];	[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)    ( < - Already mentioned above)

Doesn't the ";" added in front of the line mean disabled/not parsed text?

> **koenn]As said before, the statements in your **/etc/apt/sources.list** are meaningless. 
replace the sources.list on one of the clients with this:

```
deb http://your.server.ip.address:9999/Default/ edgy main restricted universe 
deb http://your.server.ip.address:9999/Default/ edgy-updates main restricted
deb http://your.server.ip.address:9999/Default/ edgy-backports main restricted universe 
deb http://your.server.ip.address:9999/Default/ edgy-security main restricted universe

```[/quote]

You mean getting rid of all the contents of the file "**/etc/apt/sources.list**" & running an update with _only_ the above 4 lines instead?

[quote=koenn]Make sure you use the correct IP address in stead of your.server.ip.address. 
The correct IP address is NOT 127.0.0.1[/quote]

I thought that the "server's.ip.address" was supposed to be the "localhost" - i.e. 127.0.0.1...
I thought I found this in the HowTo... 
So, which is the correct IP to use & where do I find it?
I noticed that the file ""**apt-proxy-2.conf**" has this line:

[quote=dvarsam] said:**
> 

But the "address" line is NOT parsed since there is an ";" in front.
And that ";", turns the command into plain text/comment.
Should I remove that ";" from the front & then use that IP (i.e. 192.168.0.254) as the server.ip.address?

[quote=koenn]See if it works.
Sure, but I need some guidance on the exact steps...
Please clarify the above, cause without those I can't move on.

Thanks.

---

### Post by koenn on 2007-01-31
> Which specific part are you talking about?
this one :
[http://ubuntuforums.org/showpost.php?p=2084842&postcount=73](http://ubuntuforums.org/showpost.php?p=2084842&postcount=73)
> Quote:
Originally Posted by koenn
That doesn't make sense at all, do you have a sources.list (synaptic / software properties media list) that has entries like  [ Code: deb [http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/](http://127.0.0.1:3142/gr.archive.ubuntu.com/ubuntu/) edgy ] or something equally meaningless ?

-----
> But if you take a clear look on the file "apt-proxy-2.conf", that line is disabled:
OK, I missed the ; . Enable it again, and still remove that "( <- Already mentioned above)" thing

----
> You mean getting rid of all the contents of the file "/etc/apt/sources.list" & running an update with only the above 4 lines instead?
Yes. 

--------
> I thought that the "server's.ip.address" was supposed to be the "localhost" - i.e. 127.0.0.1...
*sigh* 
For someone who was going to "invent" a centralised repository system for a local network, ignoring existing sollutions in the process, you seem to have rather limited knowledge and understanding of basic network concepts.
 
*deep breath*
127.0.0.1 is an address that is never really part of a network. It is used to test network functions on 1 machine (aka locally, hence the name 'localhost' or (local) loopback). You're testing between a server and a client, on separate machines; you need a real network, with real ip addresses. 

> So, which is the correct IP to use & where do I find it?
the correct ip address is the  ip address of the machine where you installed apt-proxy. After all, that's where the packages are (or will be), no ?  How were you going to find the ip address in your proposed sollution ? I thought you said it was going to be easy ? 
Oh well ...
run
```
ifconfig
```
on the server (the server is the machine where you installed apt-proxy). 

-------------
> noticed that the file ""apt-proxy-2.conf" has this line:

;address = 192.168.0.254

But the "address" line is NOT parsed since there is an ";" in front.
And that ";", turns the command into plain text/comment.
Should I remove that ";" from the front & then use that IP (i.e. 192.168.0.254) as the server.ip.address?

I think you don't need to state the address so the ; can remain there. It serves as an example that you *can* state an ip address if needed.
You can also remove the ; . In that case : wouldn't you think it makes sense to replace the address in the file with the correct server ip address, the one you also need for the sources.list ?

---

### Post by dvarsam on 2007-01-31
I performed the following steps:

1. On the Server PC, I edited the file "**/etc/apt-proxy/apt-proxy-v2.conf**"

2. Under the section ";; Server IP to listen on", I added the line:

> address = 192.168.1.2

Note: This was the "eth0" which I found using the command "ifconfig" you provided.

3. I restarted the program "apt-proxy" using the command "**/etc/init.d/apt-proxy restart**"

4. I went on the _Client_ PC & replaced the "**/etc/apt/sources.list**" file contents with the following (you suggested):

[quote=koenn]deb [http://192.168.1.2:9999/Default/](http://192.168.1.2:9999/Default/) edgy main restricted universe 
deb [http://192.168.1.2:9999/Default/](http://192.168.1.2:9999/Default/) edgy-updates main restricted
deb [http://192.168.1.2:9999/Default/](http://192.168.1.2:9999/Default/) edgy-backports main restricted universe 
deb [http://192.168.1.2:9999/Default/](http://192.168.1.2:9999/Default/) edgy-security main restricted universe[/quote]

5. I then launched _Synaptic_ Package Manager & clicked on the button named "**Reload**".

6. I waited until the Update is finished & then clicked on the button named "**Mark All Upgrades**".

7. I installed all upgrade packages.

_Questions_:

**1.** Even though I didn't get any errors, I truly wonder: Is this the correct way to perform an update?
I mean, the Client was downloading the updates & the updates were put inside the Client's "/var/cache/apt/archives" folder. Then the updates got installed.
When the install got finished, the updates remained on the Client's "/var/cache/apt/archives" folder.
Then I visited the Server to see what happened in that machine...
But the Server's "/var/cache/apt/archives" folder did NOT contain any package...??? :confused: 
I don't understand what is going on here...
I thought that "apt-proxy" turns the Server into a Central Internal Network Repository...
**a.** Shouldn't the packages be available over there too?
**b.** And shouldn't the Client delete its "/var/cache/apt/archives" folder's contents?

**2.** You have previously said that the Clients update automatically & nothing is required from the user - i.e. an update made manually...
But I did this manually...!!!
IF I hadn't performed above **Steps 5-7** above, the Clients would have NOT upgraded... :confused:

**3.** I noticed that on the Client's side you suggested the "/etc/apt/sources.list" file contain Repos in the following syntax:

[color=blue]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=red]Default/[/color] edgy-backports main restricted universe
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=red]Default/[/color] edgy-updates main restricted
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=red]Default/[/color] edgy-backports main restricted universe 
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=red]Default/[/color] edgy-security main restricted universe
[/color]

What is this "/Default" part you are using?
I don't understand what is going on here....?
Everything is "baptized" [color=red]Default[/color]...
So, If I want to add this Repo too:

[http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian)

I add it in the following manner?

deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=red]Default/[/color] skype

OR

deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=red]download.skype.com/linux/repos/debian[/color]

Which is the correct notation?
Sorry man, but you have lost me totally... :|

Thanks.

P.S.> I am really NOT sure whether the Client has updated using the Central Internal Network Repository (i.e. using the Server through "apt-proxy") **OR** updated plain by itself (as previously)...
How can somebody _verify_ if the Client has used the Server Repos instead of updating by itself?
I have NO clue how to check this...

---

### Post by koenn on 2007-02-01
see how easy it is ? you got it to work without knowing how it works. :)

>  Even though I didn't get any errors, I truly wonder: Is this the correct way to perform an update?
You prefer to get errors just to be sure it is not working ? 
Yes, it is supposed to work that way. In stead of downloading from gr.archive. ..., the client pc downloaded from your server. On the server, apt-proxy downloaded the packages on the fly, and now keeps them for the next client that wants them. 
This way, the way apt (Synaptic) normally works, is preserved, while you still get your 'central repository'. or: the desired result from minimal changes. Quite elegant, don't you think ? 

The Server's "/var/cache/apt/archives" folder doesn't contain any package, because that's not where apt-proxy keeps them. /var/cache/apt/archives is where apt puts packages and that has not been changed by installing apt-proxy . Look for cache_dir = /var/cache/apt-proxy in the apt config file. It indicates where apt-proxy keeps its downloads. You should find them there : /var/cache/apt-proxy is your repository. It will contain the packages you've installed, organised in folders the same way they're organised on a real Ubuntu  download server.

> 2. You have previously said that the Clients update automatically & nothing is required from the user - i.e. an update made manually...
But I did this manually...!!!
The way apt, synamtic, etc works has not changed (see previous answer), so the normal update notifications, updates, etc should all still work as they did before. 

> 
What is this "/Default" part you are using?
The "/default" in deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)**Default**/ edgy-backports main restricted universe refers to the **[Default]** section in /etc/apt-proxy/apt-proxy-v2.conf so that apt-proxy knows you want the packages to come from the backend servers listed under [Default].
Nothe that there is a number of similar sections. If you were installing or updating debian machines, you'd put  [http://192.168.1.2:9999/](http://192.168.1.2:9999/)**Debian**/ in sources.list so the backend servers under [Debian] would be used. And so on. Look back and forth between the to files, you'll get it sooner or later.

> [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian)
(If replaced that URL with [http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb) because that's the one I found working. )
This is a bit more advanced, because the skype download server is not really an official ubuntu repository. There's a number of ways to do it.
A/ you could create a section [Skype] in /etc/apt-proxy/apt-proxy-v2.conf, put ```
http://www.skype.com/go/getskype-linux-deb
```
 as backend server under that section, 
and on the clients add ```
deb http://192.168.1.2:9999/**Skype** **./** 
```in sources.list / synaptic download locations. 
First, note how the sorces URL relates to the section name, as explained before. Also note the  ./  That's because apt and apt-proxy would normaly expect an Ubuntu/Debian style directory on the server, but skype doesn't follow it. You can consider the ./ a workaround.

B/ If you can do this for one package, you can do it for many packages. Therefore, you could create a section [mixed]  (refered to by the clients with deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)**mixed** ), and list a bunch of different backand servers there (in the apt-proxy config file !) :
[http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)
[http://www.coolwebsite.com/download/linuxvirus.deb](http://www.coolwebsite.com/download/linuxvirus.deb)
[http://www.kitchensink.org/packages/spiritinthesky.deb](http://www.kitchensink.org/packages/spiritinthesky.deb)
...
...


method B is more complex and for it to "always work" you need to understand the directory tree of the repositories, in order to create the correct statements - remember that this is because these repo's don't use the standard debian/ubuntu repository directory tree.
I wouldn't recommend this until you really understand what's going on.

Look through /etc/apt-proxy/apt-proxy-v2.conf ; you'll notice that the ubuntu maintainers have added lots of sections for all kinds of repo's (skype, automatic, ...) already, so all you'd have to to in most cases is just enable these by adding lines to sources.list on the clients. 


And before you ask : what about the server itself ?
same thing as all other clients : the server, the pc running apt-proxy, could use the exact same sources.list as all the clients ; the synaptic on the server will happily talk to apt-proxy  on the same machine to get its updates from its apt-proxy cache. Another effect of the client-server architecture I meantioned a few posts back. That's _real_ simplicity. Sooner or leater, you'll learn to appreciate the beauty of it  - and to respect the developer who was intelligent enough to make something so effective that simple  :)

---

### Post by dvarsam on 2007-02-02
Dear "koenn",

Thank you for your time.
You have helped me a lot!

However, there is a lot to discuss here...
So, bare with me cause I have a lot of questions...

_Questions_:

**1.** By default, the file "**/etc/apt-proxy/apt-proxy-v2.conf**" includes the following Repos:

```

[debian]
backends = 
	http://ftp.us.debian.org/debian
	http://ftp.de.debian.org/debian
	http://ftp2.de.debian.org/debian
	ftp://ftp.uk.debian.org/debian

[security]
backends = 
	http://security.debian.org/debian-security
	http://ftp2.de.debian.org/debian-security

[ubuntu]
backends = http://archive.ubuntu.com/ubuntu

[ubuntu-security]
backends = http://security.ubuntu.com/ubuntu

;[openoffice]
;backends =
;	http://ftp.freenet.de/pub/debian-openoffice
;	http://ftp.sh.cvut.cz/MIRRORS/OpenOffice.deb
;	http://borft.student.utwente.nl/debian

;[apt-proxy]
;backends = http://apt-proxy.sourceforge.net/apt-proxy

;[backports.org]
;backends = [color=blue]http://backports.org/debian[/color]

;[blackdown]
;backends = http://ftp.gwdg.de/pub/languages/java/linux/debian

;[debian-people]
;backends = http://people.debian.org

;[emdebian]
;backends = http://emdebian.sourceforge.net/emdebian

;[rsync]
;backends = rsync://ftp.uk.debian.org/debian
```

What do you do with the above?
You just delete them?
You keep them as is?
You de-activate all of them?

**2.** Not only that, but using my assigned Repo:

```

[Default]
backends =
	http://gr.archive.ubuntu.com/ubuntu
	[color=blue]http://security.ubuntu.com/ubuntu[/color]
	http://gr.archive.ubuntu.com/ubuntu
	http://archive.ubuntu.com/ubuntu 

```

The above line 2 is a double post with previous **pre-included** Repo:

```

...
[ubuntu-security]
backends = [color=blue]http://security.ubuntu.com/ubuntu[/color]
...

```

So, does this double post need to exist?
And should each of the above lines be separately stated?
I.E.:
```

[Archive]
backends = http://gr.archive.ubuntu.com/ubuntu

[Security]
backends = http://security.ubuntu.com/ubuntu

[Gr-Archive]
backends = http://gr.archive.ubuntu.com/ubuntu

[Whatever...]
backends = http://archive.ubuntu.com/ubuntu 

```

Why should these be bundled?
OR why should these be separated into diff categories?
What are the advantages & disadvantages?

**3.** A problem exists in the following case:
```

[Mplayer-386]
backends = http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer-386_1.0-pre6-0.3ubuntu6.2_i386.deb

```

**a.** The above file _assumes_ that all my Ubuntu Networked PCs are 386 machines!
Why do I assume that _all_ Clients & Servers are 386 machines?
What IF some machine is a 586, another is a 686, another is amd64, etc etc?
The above Repo would NOT work, would it?
(i.e. I am installing a program designed/created for 386 PCs, but NOT all my Networked PCs are 386 PCs...)

**b.** BTW, I don't even know how to recognize/check what each machine is...
I never bothered to care/check what I have...
Since this suddenly is becoming an important issue...
The question is: How can I find what each Network machine is?
(i.e. launch a Terminal & type what command?)

**4.** Regarding the package "[color=blue]deluge[/color]":

IF you visit the Site [http://deluge-torrent.org/wiki/Downloads](http://deluge-torrent.org/wiki/Downloads), you will notice the following:

There is NO **.deb** file to download!!!
So, I am supposed to add a link that downloads **.tar.gz** files?
Does "apt" support **.tar.gz** files?
What do I do in such cases?

P.S.> The site says: "As of Feisty, Deluge is in Ubuntu's universe respository."
The problem is what do I do for now...?

**5.** What happens if the **.deb** file _requires/assumes_ a previous install of libraries in order for it to get installed?

Downloading a single **.deb** file would NOT work!!!
Would it?
Don't I need to add the Address of that library too?
_Example_:
Adding:
[http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/](http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/)[color=blue]mplayer-386_1.0-pre6-0.3ubuntu6.2_i386.deb[/color]

Is more restrictive, compared to:

[http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/](http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/)

The later is more "vague", but serves the purpose/case when the libraries are incorporated in the same folder!
But what IF there are also **.rpm** files lying in that folder...?
How will my Repo understand what program I want to install from all the ones lying in there?

**OR** do I need to also add lines like:

[http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/](http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/)[color=blue]library1.deb[/color]
[http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/](http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/)[color=blue]library2.deb[/color]
[http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/](http://si.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/)[color=blue]library3.deb[/color]
etc. etc.

I need to know the dependencies too?
(oh my goodness... ](*,))

**6.** What do I do with this?

```

[Backports]
backends =
	[color=blue]http://archive.ubuntu.com/ubuntu edgy-backports[/color]

```

This is too vague...
It does NOT point to anywhere specifically...
And it is also a different address, when compared to the [color=blue][Backports][/color] that came pre-installed in the "**/etc/apt-proxy/apt-proxy-v2.conf**"
file...
(go and compare the "blues"...)
What do I do?
Do I keep _both_?
IF one of them, which of the above?
How am I supposed to know which is better?

**7.** On the **Client Side**, I am supposed to add the following:

deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Default/[/color] edgy-backports main restricted universe
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Default/[/color] edgy-updates main restricted
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Default/[/color] edgy-backports main restricted universe
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Default/[/color] edgy-security main restricted universe

And I also need to add:

deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]W32_codecs ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Mplayer-386 ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Automatix ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Deluge ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Easycam2 ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Ntfs-3g ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Tapioca ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Frostwire ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Skype ./[/color]
deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]Backports ./[/color]

Isn't it better, instead of having to type 10 times the above, to do the following:

On the **Server Side**, create a category named [color=blue][All-together][/color] & then on the **Client Side**, add a single line like this:

deb [http://192.168.1.2:9999/](http://192.168.1.2:9999/)[color=blue]All-together ./[/color] :-({|=

I mean, I can save time when I only have to add a single line instead of 10 separate ones...
Can I do this?

**8.** Today I performed an "update" on the Server.
I downloaded & installed 3 packages:
  
a. libgtk2.0-0
b. libgtk2.0-bin
c. libgtk2.0-common

You said that all downloaded packages should be lying inside the "**/var/cache/apt-proxy**" folder.
But the above ones I downloaded, are lying inside the folder "**/var/cache/apt/archives**" folder.
What is going on here?
Do I have to import these files in **/var/cache/apt-proxy** _every_ time I perform an update?
... cause if this is the case, it totally "sucks"!

Thanks.

P.S.> You see, things are NOT as easy as they seem to be...
A lot of questions arise... :)

---

### Post by djamu on 2007-05-05
Jeez. why make things so complicated :shock: 

By far the easiest to implement this is >
mount -t cifs //yourservershare/archives /var/cache/apt/archives
whenever needed.

Or even better, add this to fstab.
To prevent filelocking, ( only one client can access / update at a given time )
use the "veto" switch in your smb.conf

```


[archives]
comment = mkfs-test
path = /yourpath/archives
public = yes
writable = yes
browsable = yes
create mode = 0777
directory mode = 0777
guest ok = yes
[COLOR="DarkOrange"]veto oplock files = /*.deb/*.DEB[/COLOR]


```


my five cents 
vote simplicity

:lolflag:

---

### Post by dukebytes on 2008-07-19
This is a great idea.  It would also make using APTonCD very easy for the no access machines...


duke

---

### Post by madjr on 2008-07-19
i think i seen this idea in brainstorm, the pics/mockups make it easier to understand and implement

---

### Post by songshu on 2008-07-19
sorry but this is ridiculous.

1) please give me the use case where you have 20 desktops and no server

2) you could always keep one of the desktops running all the time and use it as a server (ubuntu is quit well equipped to do that

3) why do you need a difficult GUI way if there is am easy 4 step way to do it command line? i can do this before you even had time to go through the menus, click on the application and wait for it to start ;)

**apt-cacher**

```
# apt-get install apache2


# apt-get install apt-cacher

```

```
# nano /etc/default/apt-cacher

and set AUTOSTART=1 

/etc/init.d/apt-cacher start
```





All that is left to do now is to edit the sources on every machine
```

# nano /etc/apt/sources.list
```

and change it to look like this

```
deb http://192.168.1.12:3142/security.debian.org/ etch/updates main contrib
deb http://192.168.1.12:3142/ftp.nl.debian.org/debian/ etch main contrib non-free

deb http://192.168.1.12:3142/www.backports.org/debian etch-backports main contrib non-free
```


For the ubuntu desktops we change it to this

```
deb http://192.168.1.12:3142/archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://192.168.1.12:3142/security.ubuntu.com/ubuntu gutsy-security main restricted universe
deb-src http://192.168.1.12:3142/security.ubuntu.com/ubuntu gutsy-security main restricted universe
deb http://192.168.1.12:3142/archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://192.168.1.12:3142/packages.medibuntu.org/ gutsy free non-free

```

---

### Post by djamu on 2008-07-19
:lolflag:

If I may add to previous post that by installing apache(2) alongside apt-cacher you get a nice interface ... ( [http://localhost/apt-cacher](http://localhost/apt-cacher) )

also notable is that there's a C rewrite called apt-cacher-ng

personally i find my method the easiest ( sharing & mounting /var/cache/apt/archives across macines ) as even less keystrokes are needed :)

---

