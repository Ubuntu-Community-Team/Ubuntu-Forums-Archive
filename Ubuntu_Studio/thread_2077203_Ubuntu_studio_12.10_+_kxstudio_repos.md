---
title: "Ubuntu studio 12.10 + kxstudio repos?"
date: 2012-10-28
forum: Ubuntu Studio
---

### Post by bumBumBUM on 2012-10-28
Is this a good idea?

I just moved over from avlinux and I am relatively new to ubuntu. I tried the full-on kxstudios as well as dream studio but have settled on ubuntu studio.

Is it currently possible to install the kxstudios repos over ubuntu studio 12.10?

I noticed that they have a quantal section with newer packages for things like guitarix (but also some crucial ones such as jack jackd etc) but I have found no official word on whether it's compatible or not yet. As such I'm not sure if it's wise to mess with this seeing that ubuntu studio is currently working ok for me. I did read a previous forum post with the same question for a much older release but I haven't been able to find any up-to-date information and the answer to the post was ambiguous.

So...

What are the benefits?

How does sharing packages work with with regard to the ubuntu studio release cycle vs. kx studio's?

Are their any disadvantages?



Also, if anyone is rocking an up to date ubuntu studio + kxstudio repos hybrid I would be glad for any experiences.

thanks,
bum Bum BUM

---

### Post by sgx on 2012-10-28
Hi, the question isn't 'what does KX provide', rather,
'What am I unable to do, that I need/want to do'.

The fence between us, and the greener pasture,
will always be barbed wire, but covered with pretty flowers,
with a maiden beckoning from the other side, 'More, better, faster, newer, shinier'...

Keep what works, create music, and test safely,
installing test distros and add-ons on external drives,
or expendable media.

If money is too tight, do one last fresh install, and create
a separate /home partition, so time is saved in future reinstalls,
by re-using window-manager, internet, and eye-candy settings.

A lot of work has gone into KX, to make linux audio better.
Certainly worth an hour in google to see what it provides,
and difficulties it solves.

It helps to stay familiar with 3 or 4 working environments,
and keep a full backup of crucial things, at a remote location,
where thieves, fire, floods etc can't take you down.
Cheers

---

### Post by CrocoDuck on 2012-10-28
Hi. I used kxstudio repos to try their realtime kernel on ubuntu 12.04 (the kernel was not able to boot...). Of course you can add the repos, but I suggest you to add their repos only if you are sure that it will not implies dependencies issues, that probably are around the corner if you installed ubuntu studio (to avoid problems I disabled the kxstudio repos after had purged the unworking kernel). kxstudio is a great collection of software, but to have a well made system I suggest you to go through a net boot installation (if you had gained the experience you need to do this). There are a lot of software that you can download from the site and manually install, like tons of plugins, without needing to add the repos. If you are interested in some specific program you don't have remember that you can download a single deb from their site. In my opinion what you can do with the software included in ubuntu studio is basically esactly what you can do with kxstudio's software...

---

### Post by sgx on 2012-10-28
links to get usb-stick test install media ready:

[http://www.linuxliveusb.com/en/download](http://www.linuxliveusb.com/en/download)

[http://www.pendrivelinux.com/create-...per-partition/](http://www.pendrivelinux.com/create-...per-partition/)

[http://www.unetbootin.sourceforge.net/](http://www.unetbootin.sourceforge.net/)

---

### Post by bumBumBUM on 2012-10-28
thanks for the replies,

As I can see it (no one has really contradicted this yet) the main benefit of the kxstudio repos is the updated packages/plugins and also slightly modified versions - how they are modified exactly I still don't yet know... My impression from this thread (though no one has said it outright) is that by adding the repos and updating packages to the kx versions, if my system doesn't break now it should do so eventually.

However, the original post by falktx regarding the kxstudio repos states that they should be compatible with ubuntu derrivatives - though this info has not been updated to include the new quantal release I expect it will eventually be the case. I imagine that prioritizing the repos and pinning packages might safely take care of possible issues though and would still provide easy apt-get and synaptic access to all the packages.

Generally speaking though, I'm in no rush to upgrade - I'd much rather have a working system than a bleeding edge one. In fact, I have only moved from avlinux because I need better support for my new laptop and the last two versions of AVL suffered many many incompatibilities with my new hardware. It's not because I've got the upgrade fever, I just don't want to have to try too hard to make things work and if the system breaks then I want to be able to quickly reinstall everything from memory in a matter of a couple of hours tops. Honestly AVL6 is awesome and I would have been happy to stay with it - I still have it on usb key and its installed on my old netbook, it was my first love as far as linux audio is concerned.

So I happen to have bought this laptop at the same time that avl was updated to its final version, as well as ubuntu studio to 12.10 and soon kxstudio maybe. Since then I have spent a week with AVL6, a few days with kxstudios, over one month with dream studio and have now settled for ubuntu studio (installed since almost a week and a half).

Dream studio was 100% compatible but I eventually discovered that my humble laptop was not powerful enough to run unity effectively while doing intensive low latency stuff. I was gutted because it really did work out of the box. The unity stuff wasn't actually very productive though as in practice it got in the way much more than it actually helped. I did have a few issues with ubuntu studio but now it's running smoother than AVL or dreamstudio ever did(except for 1 small  bug i just noticed). It even has some advantages such as the the xfce settings editor which lets me make it so that with either jack running or not and with headphones or even usb audio device, my laptop's volume buttons will change the output volume.... it's a simple thing but I think it's amazing. Also the way XFCE lets you move windows around, between desktops or just with tiling is really effective on my 11inch screen. I had to learn the whole pulse audio ******** though as well as get used to XFCE, kde and Unity/gnome 3 in the process but now I'm happy.

When I installed kxstudio, I tried different desktops and kernels and installed it all via the netboot ISO but found that it was almost as incompatible as AVL6 and thus not worth the effort. As such I didn't really get a chance to register its pros and cons regarding the software (aside from a quick poke around falktx's own apps). What has been made clear in the last couple of years though is that the newer/newest versions of guitarix and ardour etc. are definitely worth getting. As such, I am still curious as to what's there and if it can be done.

That said, this clearly not a case of the grass being greener - I would still just honestly appreciate some specific insight in the benefits of the KXstudio apps to know whether It's something that would benefit my usage scenario or not. I'm still learning so having a bunch of stuff available is great for when I'm not being productive and just want to poke around. For me, it's an important part of the learning process as it gives me ideas for further down the line. That is why I am curious about the kxstudio repos. If I had to look on google for specific apps and plugins and know what to look for in advance I would never have got as far as I have done (how do you look for something when you don't know that it exists?).

So, if anyone has more experiences or information about it actually being viable or not, as well as any specific benefits I would be grateful to hear more as I've been living on the AVLinux island for a while and uptodate information on ubuntustudio/kxstudiorepos is sparse and still very new to me.

thanks again

---

### Post by sgx on 2012-10-29
From a distance, it appears falkTX has invested, at no small personal
expense, in claudia, cadence, and several other tools to simplify session mamagement, plugin use, configuration, system integration, and overall ease of use. Not to mention beating the fine
TAL plugins into linux usability, and compiling things uniformly.

I think potential dependency issues can be delt with by using
the graphic environment he does, and comparing dependency notes
between his repos, and those of your base system, before updating. 

Also comare dependencies with debian unstable, there are a few
broken combinations in the wild. gnome virtual file system,
and gnome canvas, are not uniformly implemented/bug-free.
I doubt d-bus and hal are always trouble free, and of course
pulse Vs the world  yada yada :guitar:

I now stick to small and fast E17, on top of kde4,
its got great themes, several icon sets, flexible placement
of gui elements, and recovers from most faults with a keystroke,
and no data losses.(pounds furiously on nearby wood)

When the snows come, I may try these new tools, but I am
of that old school, what ain't broke, don't get fixed :)

As an experienced user, you know the drill if things get
upside down, and already have alternatives in place.
KX should be easy money.

I really hope a barebone Ubuntu Studio will be supported someday,
I think it would reduce the number of issues new users face,
and slightly broaden the compatibilty base, helping those
using limited computer resources. A full-on guitar distro,
could easily iso under 300 meg, no need for dvd sizes.
Cheers

---

### Post by maciekpruski on 2012-10-29
Hi,
I have 12.04 + KXStudio on top and it is a good combo, I think well worth it. I read on the linuxmusicians kxstudio subforum that they are working to have everythink ready for 12.10, maybe it is available already.

I think kxstudio uses a different version of jack and has the additional software like cadence, klaudia etc. that can help with session management. They also provide kernels if I'm not mistaken. It runs pretty good on my laptop that isn't very powerful

---

### Post by bumBumBUM on 2012-11-04
thanks for all the input.

I will be sticking where I am with vanilla repos as everything runs perfectly at the moment (since I managed to squash the one little niggle I was having). I will be checking out kxstudios little by little to have a look at what I'm missing though.

thanks again

---

### Post by macinnisrr on 2012-11-19
Sounds like you'd like Dream Studio for Ubuntu ([http://www.dickmacinnis.com/dreamstudio/dream-studio-for-ubuntu/](http://www.dickmacinnis.com/dreamstudio/dream-studio-for-ubuntu/)). It works with any Ubuntu derivative (like Ubuntu Studio), includes all the KXStudio repos AND Dream Studio repos, and is super easy to install.

---

### Post by bumBumBUM on 2012-11-22
> **macinnisrr said:**
> Sounds like you'd like Dream Studio for Ubuntu ([http://www.dickmacinnis.com/dreamstudio/dream-studio-for-ubuntu/](http://www.dickmacinnis.com/dreamstudio/dream-studio-for-ubuntu/)). It works with any Ubuntu derivative (like Ubuntu Studio), includes all the KXStudio repos AND Dream Studio repos, and is super easy to install.

thanks Diçk, I did say in one post above that I had given dreamstudio a thorough test (it was my main OS for over a month). I also noticed the recent dreamstudio update and went back to take a look.

Unfortunately, whilst my humble computer looked great with unity for day-to-day things I discovered that it was not so great when under the load of realtime audio... To the point of interrupting what I was doing and affecting overall stability. Having only a small screen also means being able to switch windows is vital - I can do this in xfce without a blink while under heavy load but unity was definitely a no go in this area (up to five second delays to switch between workspaces with as much eye-candy switched off as possible).

I have to say that I was gutted to realize that I couldn't stay with dreamstudio as until then everything had been going very well.

In any case, great work and thankyou for sharing it!

edit: thought it might be helpful to list the specs of my computer - I have 11,6" laptop with amd e-450 dual core 1.65ghz processor / radeon 6230 mobility graphics / 4gb ram. I tried both open source radeon driver (with 3.4 + kernels) and amd's closed source cataylst drivers. The newer kernels' radeon drivers and the catalyst driver did make unity very snappy but the improvement was lost in realtime/heavy load conditions.

---

### Post by Precipitous on 2012-11-28
@bumBumBUM:  I have had great success mixing the KX Studio repos and Ubuntu Studio. What I normally do is start with a clean vanilla install of Ubuntu, then I install Synaptic (I find it a lot easier to use than the Ubuntu Software Center), then add the KX Studio repos. Next I install all of the KX Studio packages I want like jackd, cadence, etc. Finally I install all of the the Ubuntu Studio packages. 

This gives me the best of all three worlds. The Unity interface I like, the KX versions of common audio apps, the KX specialty apps and the Ubuntu Studio suite of everything else...

Cheers!

---

