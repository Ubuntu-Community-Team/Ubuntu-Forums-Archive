---
title: "Help with partitioning a 4gb drive for hardy, keeping OS + data apart"
date: 2008-05-27
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-27
Hello everyone 
I've read loads of guides and still don't know what the best way to partition my OS drive.
It's a 4.3 gb IDE drive which I want to completely contain the os. I hvae all data on another 3 IDE drives totaling around 250GB. When I use guided partitioning Ubuntu is giving me 256 mb of scratch space. 
I have 256MB of ram (I'm upgrading to 512mb or 1gb v.soon). From what I've heard it should be roughly twice / three times the size of your RAM. 
I then have 1.1 GB of unused spac. I still have amule, torrentflux, swat, mythTV to install.
Will all this fit on the 4GB? I may want more apps in the future to. Shall I put the OS on one of the other drives (next one up is 40gb)?
Even better how do I set it up so I have the OS / Swap on the 4gb and the data directories (home etc.) on the 40GB. That way I can reinstall the OS and still keep the data partitions intact.
I find the partition setup app on the installer very confusing.
Can someone plz give me instructions specific to my situation.
I have a 4gb, 40gb, 40gb and an 80gb in box as IDE. I will have a lot of torrents file and movies, websites that I work on, general family stuff and directories for each family member. Just thought I'd give an overview of how the drives will be used in case it helps.
Thanks for all your help guys.

Gareth

---

### Post by wdaniels on 2008-05-27
4GB should be enough for the OS and any applications you need, but it's close so I would suggest you consider putting the swap partition on another drive (this is better for performance also) and make it bigger. Assuming you're less short on space on the other drives, I'd go with 1GB for swap.

Try the guide [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") for setting up the home partition.

---

### Post by NateMan on 2008-05-27
just install the root file system on that drive, move swap to your fastest drive, then mount the other drive partitions in or as your home directory. I normally mount each drive as a separate folder in my home directory and then use symbolic links and file permissions to allow the different users access to it all. Symbolic links are your friend for managing a family's worth of usernames and files, some of which everyone needs access to, some of which only you need. Plus when those drives are mounted in your home directory as their own folder then you can reinstall and not loose data. For you since your os drive is so small, mount one of the other drives as your home directory so that accident copies not into the symbolic links will not end up on your os drive. Use one 40gig for your home directory and then just use links for the rest. That drive should also probably hold your swap file. Hope that helps!

---

### Post by garethsimpsonuk on 2008-05-27
Thanks for the reply, yes on a different partition would be quicker only if it's on a disk on a second IDE cable otherwise I think it actually slows it down.
I only have 1GB left on the 4GB (I have a dieted down gnome installed).
I think it would be better to have the swap  + os on the 4gb and partition the 40GB for my home / data. I only have a small file server so a seperate swap isn't really necessary.
I'll check the link, thanx

---

### Post by NateMan on 2008-05-27
Why are you running gnome on your server? That's a complete waste on any server drive, much less a 4.3gig drive. The separate swap wasn't intended really for speed, but to conserve space. So is this a server or a desktop?

---

### Post by garethsimpsonuk on 2008-05-27
Thanks for the reply, yes on a different partition would be quicker only if it's on a disk on a second IDE cable otherwise I think it actually slows it down.
I only have 1GB left on the 4GB (I have a dieted down gnome installed).
I think it would be better to have the swap  + os on the 4gb and partition the 40GB for my home / data. I only have a small file server so a seperate swap isn't really necessary.
I'll check the link, thanx

---

### Post by wdaniels on 2008-05-27
Sure, 256MB is not a lot to loose from the 4GB root partition, and would probably be OK, but I'd still rather give it to the root partition - add a few kernels, development headers then a big upgrade into apt's package cache and you'll soon start cursing that little swap partition.

---

### Post by garethsimpsonuk on 2008-05-27
But I know I wont ever do that, but I see your point on swap on a different drive.

So is this the correct way of doing things?

- Install '/' and swap (1GB) to 4GB (root=ext3, swap=..forgot, the standard filesystem I guess)
- Install 'Home' to 40GB with ext3

Will this be the right way? I'm sat here waiting to install Ubuntu again but I don't want to use the guided method, but I'm confused about the manual. 
Will this way sort out all the /etc etc. into the 4GB automatically?

Thanks

---

### Post by garethsimpsonuk on 2008-05-27
Sorry nateman I missed your post. I have Gnome because I saw Ubuntu for the first time 2 weeks ago., and I'm easing the learning curve. 
I only start x when I need to and try to use the command line. I have it stopped properly (+ other unneccessary sevices) so it isn't really any slower than the standard cli enviroment.
I think people should who are experienced should tell this to noobs who are always saying ' I want a GUI', rather than saying it's uneccessary. My setup means I down have the uneccessary services running but if I need them I can start them. I had to find all this out myself. If I get the oppourtunity to give advice on a server GUI this is what I wil tell them, the pros / cons and possible solutions.
While I'm here quick question. If I have services properly stopped, (such as gnome) this can't surely be a security threat until I start it?
Thanks again guys

---

### Post by NateMan on 2008-05-27
Ok first things first there is a much better way to ease the learning curve. Its a webbased gui called webmin. Much lighter and works better for server configuration than gnome. Gnome takes up a good bit of space better reserved for other things. Also what wdaniels said about the swapspace is 100% on the money and you will do the things he was talking about on at least a monthly basis when you update. Updates can be big! I wouldn't give out advice about running a gui server when you haven't figured out how to manually setup partitions and run a server. I've had numerous buddies setup their own servers, install a gui, and then have problems, forcing me to come over and immediatly ignore all of the gui and open a terminal window.  Bad advice is much worse than no advice. Have you tried to follow the perfect server guide yet? It is where everyone should start on a ubuntu server. [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) is the link. Plus can't someone who actually gets into your server start gnome, plus there are numerous packages gnome installs worthless in a server environment. 

Now for how to do the manual partitions:

set your 4gig to be /
mount your 40gig as /home and put swap on it. (data density on the drive will improve swap performance)
now mount your other 40gig and 80gig drive in either /media or /home and then place symbolic links where needed in the folders.(I would use /home/40gig and /home/80gig or /media/40gig /media/80gig) You can make sure at this point that your data will be saved as well. Good luck with the partitioning. And remember "Symbolic links"!

---

### Post by garethsimpsonuk on 2008-05-27
- I have webmin because I will eventually be running headless
- Space isn't an issue to me I can afford it
- I never disagreed with wdaniels, I said 'I see your point'
- I said when I have the oppourtunity to give advice I never said I am, n e ways if it's bad advice or not I would clearly state it's my opinion and I will state that I don't know that much, I've only used Linux for 2 weeks ffs.
- Did I say I'm 'giving' advice on partitions...no, I'm 'asking'. Doesn't mean my advice on GUI's isn't any good.
- Because I don't know how to do advanced partitioning I don't know how to run a server? I already am.
- I have got that guide and others
- I use the terminal quite a lot for someone 2 weeks in.
- I said I removed uneccessary packages (of course there must be more) and thankyou that's a very good point that they could start gnome.

Thankyou for the advice, it seems a good method and I will follow. It looks like I need to research symbolic links, as I do find I have problems with setting uppublic share + private directories for each family member, and reserving a 'business direcory with restricted access

Thanks for your help

---

### Post by NateMan on 2008-05-27
Well two weeks is almost no time using it. I've never once used the guided partitioning, since in older versions it could cause more harm than good. Your reinstalling your server, right? Well then its not really running.

If I get the oppourtunity to give advice on a server GUI this is what I wil tell them, the pros / cons and possible solutions.

This shows that you think you should and could give advice. And if you have the perfect server guide, then you shouldn't have any problems setting one up. That guide is quite good. Webmin is very good as well and should be a complete replacement for your gui. I have yet to figure out what people actually DO with a server gui. You also have clearly shown that you don't have space since your using a 4gig harddrive for your os. You should try to learn more about how linux itself works rather than ubuntu. Do you know how to use find, grep, awk, or any of the other cli programs that make server administration easy? What about piping of command results to other commands? There is seriously a huge learning curve to become a good linux administrator. However, that curve can be learned, and once overcome you can go to any linux system and fully understand its filesystem, not just distro specific. I would be glad to help with anything you want to do, but a gui is just a crutch and waste of learning for servers.

---

### Post by garethsimpsonuk on 2008-05-27
*Your reinstalling your server, right? Well then its not really running.*

No it's running, yes I'm reinstalling it.

*This shows that you think you should and could give advice. *

I don't think I 'should' but I do think I 'could' some competent Linux users will agree on the method I use. It will help for a lot of ppl who are new. This is is probably why Fedora gives the option to install a GUI as default at install. Although of course a server admin shouldn't. ( I am not one of these, I am setting up a home server, I do web design and SEO. It is a bonus that I'm learning about linux as it always adds to my skillset and I can understand the roles of the guys at work, which they appreciate.)
I have plenty of space but I have choosen to exercise my right to put whatever I want in my server. I have 3 500gb drives (2 in cradles) on my desk right now, would you like a photo?
Again I have read about grep and piping but again I am not doing this because I'm an admin. If I was and I was asking these questions I think I'd be in trouble.

Feel free to post and I really do appreciate and value your advice but can we keep it to the issue I posted about. I found our lil 'debate' educating   but I'm bored of it now. I aint discussing anything other than partitions in this post.

Cheers,

Gareth

---

### Post by NateMan on 2008-05-27
Maybe you'd be better off running a desktop, and then sharing files and webhosting off of it... Besides I never saw in your post that you had 3 500 gig drives hooked up to the machine. I'm glad you've become the expert that you are in 2 weeks time.(as opposed to years...)

---

### Post by garethsimpsonuk on 2008-05-27
Anyone will tell you that the desktop isn't as good as the server version for stuff like that. I take everythning out of gnome that I think I don't need, the kernel is slightly optimised for servers so it makes sense to use that one. So maybe I wouldn't.
Have you tried to follow the perfect server guide yet? It is where everyone should start on a ubuntu server. [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") is the link

I never said they're hooked up to the machine because they're not.

I use a host in a data centre for my sites. My home site is for development and for a family site (well it was and it will be again)

I have clearly stated I'm a noob but to have some of your theories tested by someone 2 weeks (as opposed to years) in to linux should question your own 'expert' status.

This started out as an educational debate but now it's just annoying and you have lowered your standards so this will be my last post on this. I suggest you do the same.

---

### Post by NateMan on 2008-05-27
You haven't tested a single theory of linux usage. Most of your posts are full of grammatical and spelling errors and you don't seem to have any real knowledge of linux. You already knew what you were doing before you ever got any advice.  In fact its safe to say that nothing you've said is correct. You don't even know how to keep public and private data seperate (File Permissions). There is a ton of different ways to manage data in your server and you haven't even started at the basics, yet you are still questioning other people who actually know what they are doing and did attempt to help you. Even how you setup your GUI is full of mistakes. Why gnome? Gnome and kde are the two fattest desktops available. There are loads of other ones that are much better suited to a server in particular just running xwindows and adding all the different things you need in. You can even install all the gnome apps you may want for managing things graphically. Ubuntu's gnome in particular is one of the most bloated things out there. If you only knew half of what you thought you knew you'd probably be ok and wouldn't have made any of your posts so far.

---

### Post by garethsimpsonuk on 2008-05-27
search my other posts, looked at xfce openbox etc. I got an A in lang and a B in lit at skool, just because your only worth speedtyping doesn't mean I can't use the english language. 
I didn't know because I've used your advice on partitioning actually by the way.
The act you've posted again shows you've got nothng better to do and I cant believe I'm still posting (probably because you're annoying)

Thats it thats all your getting out of me Goodbye

---

