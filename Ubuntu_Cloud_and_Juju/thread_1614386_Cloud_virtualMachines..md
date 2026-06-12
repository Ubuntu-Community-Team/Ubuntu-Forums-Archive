---
title: "Cloud virtualMachines."
date: 2010-11-05
forum: Ubuntu Cloud and Juju
---

### Post by deunnero on 2010-11-05
So I've been reading about this cloud thing.  Basically from my understanding all it is, is a bunch of computers running virtual machines. 

I've created a virtual machine in virtualBox and it uses; Ubuntu Server (latest)  I removed mostly everything so now all it's got on it is mysql database server. I went ahead and gave it the database... everything works the way I want it to...

yes, I should probably just use simpleDB instead.  For now let's just roll with a database instance.  I just want to test how to get this working.

Now, I read somewhere ( I don't even know where I read this... just somewhere on the internets) I think that ubuntu uses KVM.  

How would I go about converting?  The computer that i'm messing with is a Windows pc.. I haven't found any decent tools to convert it with... the VMConvert was crap. Or atleast I couldn't find a convert (vdi) option.

or would I need to somehow upload my virtual machine to the server and do command line converting on it?

-Thanks,
Jon

---

### Post by kim0 on 2010-11-05
hey deunnero,

Not quite sure I understand your needs. My understanding is your stack is

Windows - VirtualBox - Ubuntu - mysql

right ? and you want to run that Ubuntu VM on a real Ubuntu running on a physical box ? If so, then the easiest way is to just install vbox on the physical Ubuntu too! Yes ubuntu uses KVM by default, but you can still install vbox very easily and run the same VM you run on windows

---

### Post by deunnero on 2010-11-05
Will ubuntu "instance" the virtual machine out to other computers?

I'm definitely interested in seeing what the cloud can do... 

I was hoping to atleast get the store images to work, but it looks like I won't even be able to get those to work for some unknown reason.


I get this?
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs971.snc4/76483_465035897940_555042940_5517940_1360347_n.jpg[/IMG]

---

### Post by deunnero on 2010-11-05
Ok... so further looking at this error.... I found [http://open.eucalyptus.com/forum/not-enough-resources-vm-instances](http://open.eucalyptus.com/forum/not-enough-resources-vm-instances)

it said to do  euca-describe-availability-zones verbose

and I get   EC2_Access_key environment variable must be set...

What would I set this too?

[edit]  Looked it up...  this is the Amazon EC2 key that it wants?   I'd rather keep it local/private.

[edit] new goal.....  get the store images to work. lolz.

---

### Post by deunnero on 2010-11-05
ok...looking at some log files.... 
I cleared out all the log files and rebooted.


cc-registration.log says 
> 
ERROR: You need to be on the CLC host and the clc needs to be running


axis2c.log says
> 
[error] http_Transport_utils.c(2557) service or operation not found


---

### Post by kim0 on 2010-11-10
Hey, if you're still facing technical problems, I suggest you post to the mailing list ubuntu-cloud
[https://lists.ubuntu.com/mailman/listinfo/Ubuntu-cloud](https://lists.ubuntu.com/mailman/listinfo/Ubuntu-cloud)
Regards

---

