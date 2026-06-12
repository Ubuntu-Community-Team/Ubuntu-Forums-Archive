---
title: "Possible solution to cloning my o/s into VB??"
date: 2011-05-18
forum: Virtualisation
---

### Post by ClientAlive on 2011-05-18
Hi,

For a while now I have wanted to get an exact copy of my operating system into Virtual Box. I have looked all round and the best I'd been able to come up with was clonezilla. The problem with this is clonezilla requires you to have the same amount of space where you are cloning to as where you cloned from - and I don't have the system resources for that.

So I've gotten to thinking . . . Virtual Box has a feature that allows you to take a snapshot of your o/s in Virtual Box. Supposedly the way this works is it creates a file that somehow describes the difference between a previous snapshot and the one you just made. When you go to restore from the snapshot it uses that information to make things back the way they were when you took it.

Now I don't know a lot about the details of how this works but I got to wondering if I could somehow make use of that feature to accomplish what I need. I wonder if anyone here has an idea how I would go about it.

Here's what I thought I might be able to make happen:

If I can get that tool in Virtual Box to take a snapshot of a fresh install of the same release as what I have now (Ubuntu 10.04) and then can get it to take one of my current o/s, I could somehow get it to create that snapshot file in a way that describes the difference between a fresh install and my current setup. I could then just do a fresh install into Virtual Box and then use that snapshot to transform it into an identical duplicate of my o/s (what would be considered the host o/s at that point).

What do you guys think? Does anyone know how a guy might hack this out? Would it be real involved and difficult?

Any ideas would really be appreciated.

Thanks
:)

---

### Post by ClientAlive on 2011-05-18
All I'm saying is I wonder what would be involved in trying to do something like that. Is it even worth trying to do? And what areas might I need to research to go about it if I did?

Thanks

---

### Post by CharlesA on 2011-05-18
I think VMware has a tool that can convert a physical machine to a VM, but I am not sure VirtualBox does.

From what I read, the only real way to do it is to use cloning with clonezilla or the like.

What you could do is mark whatever packages are installed and then do a clean install in the VM and install those packages.

```
dpkg --get-selections > installed 
```
```
sudo dpkg --set-selections < installed
```

---

### Post by ClientAlive on 2011-05-18
> **CharlesA said:**
> I think VMware has a tool that can convert a physical machine to a VM, but I am not sure VirtualBox does.

From what I read, the only real way to do it is to use cloning with clonezilla or the like.

What you could do is mark whatever packages are installed and then do a clean install in the VM and install those packages.

```
dpkg --get-selections > installed 
```
```
sudo dpkg --set-selections < installed
```


Right on.

I think what you are saying is that:

```
dpkg --get-selections > installed 
```

would be entered into the command line at the host system.

And that:

```
sudo dpkg --set-selections < installed
```

Would be entered into the command line at the guest system?

Is there a way to transfer configurations too?

The reason for wanting this is so if I do trial runs on the guest o/s it is closer to the actual o/s and therefore the results I get in the guest o/s would be more reliable/ accurate to what would really happen on my host o/s if I did it there.

Does that logic seem right?

Thanks

---

### Post by CharlesA on 2011-05-18
That's right. I'm not quite sure if you can transfer config that way tho.

I do know, that you can tar your whole linux install and then untar it, but I'm not sure if there are any problems that might be caused by doing that.

---

### Post by ClientAlive on 2011-05-18
> **CharlesA said:**
> That's right. I'm not quite sure if you can transfer config that way tho.

I do know, that you can tar your whole linux install and then untar it, but I'm not sure if there are any problems that might be caused by doing that.


Well the simples solution seemed to me to use clonezilla (or something like it - tar would be about the same I'm guessing). This would only work if it is possible with Virtual box to put stuff into it in that manner.

The reason this is impossible for me is that I only have a 40 gig local drive. The o/s on this thing takes up nearly 20 gig (I think the iso of it is 19.9 gig). So that's it for system resources.
-----------------------------------------------

I'm sorry Charles. I just realized something. 18 gig of that is stuff I intend to move over to my external drive anyhow and is not the kind of thing that is a factor in my reason for wanting to do this.

Maybe I can use clonezilla (or tar) after all. After I move that chunk of data off here.

I'm sorry man. I just didn't think of it until right now.

I'll give it a try.

Thanks for your help man.

---

### Post by CharlesA on 2011-05-18
S'ok. Happens to everyone.

If your external drive is large enough, you can just have clonezilla back up to it and do it that way. :)

---

### Post by ClientAlive on 2011-05-18
> **CharlesA said:**
> S'ok. Happens to everyone.

If your external drive is large enough, you can just have clonezilla back up to it and do it that way. :)

Yeah, I just did that earlier. Wonder if can take it from the usb and put it into VB. Guess I'll find out.

:D

---

### Post by ClientAlive on 2011-06-25
Well I finally, finally! got it figured out. I posted what I did that worked for me in this  [http://ubuntuforums.org/showthread.php?t=1774895&page=6](http://ubuntuforums.org/showthread.php?t=1774895&page=6)  thread in post #55.

This thing took me several weeks of asking around and searching the Internet to finally figure out. I don't know why it was so tough but it just seemed like so many things go into doing something like that.

Anyway . . .

HTH

:)

---

