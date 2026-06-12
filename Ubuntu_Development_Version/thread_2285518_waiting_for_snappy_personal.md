---
title: "waiting for snappy personal"
date: 2015-07-06
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-07-06
Sebastian Bacher tells me that the snappy personal images are not available yet and that to subscribe to the snappy/devel/list is best way to know when and where they will be ready. How to subscribe to this list ?

Regards..

---

### Post by PaulW2U on 2015-07-06
I assume [https://lists.ubuntu.com/mailman/listinfo/snappy-devel](https://lists.ubuntu.com/mailman/listinfo/snappy-devel) is what you're looking for.

---

### Post by QDR06VV9 on 2015-07-06
> **PaulW2U said:**
> I assume [https://lists.ubuntu.com/mailman/listinfo/snappy-devel](https://lists.ubuntu.com/mailman/listinfo/snappy-devel) is what you're looking for.

Yep that is it! Thanks PaulW2U.:)

---

### Post by ventrical on 2015-07-06
Thanks a mil :)

Regards..

---

### Post by PaulW2U on 2015-07-06
> **runrickus said:**
> Yep that is it! Thanks PaulW2U.:)

> **ventrical said:**
> Thanks a mil :)

I have my uses then. :p

For those that don't know, all of the official (public) Ubuntu mailing lists can be found at [https://lists.ubuntu.com/](https://lists.ubuntu.com/). 

The site is often worth a browse to see if there's a mailing list that's relevant to your interest and quite a few will be of use to those using the development version.

---

### Post by grahammechanical on 2015-07-07
1# person: "So, Snappy Personal is coming, then."

2# person: "Yeah. So, is Christmas." 

3# Me = :mad:

---

### Post by ventrical on 2015-07-07
+1 :)

 I finally get time to do some work here ... uh .. snappy core does basically ... nothing :) (jk) .. but it is a real curiosity .. and waiting for snap-personal ?? who knows .. so I will work on the wiki :) 

Regards..

---

### Post by grahammechanical on 2015-07-07
There is something happening on Ubuntu On Air. It started at 1400 UTC today (7th). It is called Snappy Open Houses. It is focusing on Snappy Ubuntu Core. It demonstrates how to flash a device and install snappy core in a KVM, how to update and how to roll back.

I do not have time at this moment to follow this UOA session. But it might be possible to do something useful with Snappy Core and gain some experience in transactional updates and roll backs. I will see what links I can put in the testers wiki. We never know, but Snappy core could the foundation for snappy personal. 

[URL="https://wiki.ubuntu.com/Snappy/OpenHouses"]https://wiki.ubuntu.com/Snappy/OpenHouses

[/URL]Regards.

---

### Post by ventrical on 2015-07-07
> **grahammechanical said:**
> There is something happening on Ubuntu On Air. It started at 1400 UTC today (7th). It is called Snappy Open Houses. It is focusing on Snappy Ubuntu Core. It demonstrates how to flash a device and install snappy core in a KVM, how to update and how to roll back.

I do not have time at this moment to follow this UOA session. But it might be possible to do something useful with Snappy Core and gain some experience in transactional updates and roll backs. I will see what links I can put in the testers wiki. We never know, but Snappy core could the foundation for snappy personal. 

[URL="https://wiki.ubuntu.com/Snappy/OpenHouses"]https://wiki.ubuntu.com/Snappy/OpenHouses

[/URL]Regards.

Sounds great!  yes .. I have already installed snappy core on qemu (kvm) and it works like a charm. However .. it is very limited to what it can do and is more or less designed for Cloud.

You can install qemu from USC or use synaptic or terminal (USC worked great for me). <we are supposed to be testing it>.

Other install qemu:  [https://help.ubuntu.com/community/Installation/QemuEmulator#Preparation_of_the_QEMU_virtual_environment](https://help.ubuntu.com/community/Installation/QemuEmulator#Preparation_of_the_QEMU_virtual_environment)

 Here's how to install it on ubuntu(flavours) [https://developer.ubuntu.com/en/snappy/tutorials/using-snappy/](https://developer.ubuntu.com/en/snappy/tutorials/using-snappy/)   .

@note to graham and team

  I have started to populate the Instructional Development section with some info from other links . Please feel free to add or contribute there, even if it is redundant from the Library section of the wiki.

Instructional Development:  [https://wiki.ubuntu.com/U+1/InstructionalDevelopment](https://wiki.ubuntu.com/U+1/InstructionalDevelopment)

Regards..

---

### Post by PaulW2U on 2015-07-07
The first Snappy Open House has been archived on YouTube at [https://youtu.be/YMJ-R7KeMr0](https://youtu.be/YMJ-R7KeMr0).

---

### Post by ventrical on 2015-07-07
I asked this question:

```

[11:56] <ventrical> QUESTION Will there be a lot of hardware obsoleted by convergence ??

```

and mHall responded - no .. that Ubuntu will still be able to be run on older hardware .. it will just not be converged. They went on to comment that the idea of convergence is to bring in newer hardware .. etc.. but most current legacy will run the ubuntu flavours.

No commit from mHall as to 'WHEN' snappy personal will be released but he did say that everyone will know ..

Regards..

---

### Post by ventrical on 2015-07-07
> **PaulW2U said:**
> The first Snappy Open House has been archived on YouTube at [https://youtu.be/YMJ-R7KeMr0](https://youtu.be/YMJ-R7KeMr0).

I had two questions answered. No commit as to "When" snappy personal will be released and that older hardware will not be obsoleted 'by' convergence --just not converged - but still able to run the usual ubuntu desktops. Didn't have time to ask about current unity7 development or if unity8 will be staple for legacy hardware.

Thanks..

Regards..

---

### Post by slickymaster on 2015-07-07
For those interested, the feedback is welcomed: [Snappy RC Testing ]("https://docs.google.com/forms/d/1dO0juM0LaWvGDKoot-jIG4_O7MYJsnOHMRIvBPoGArA/viewform")

---

### Post by ventrical on 2015-07-07
Thanks for link slickymaster.

 I just updated from an install of 1 month ago and all worked well on the kvm. I am going to start another thread for those who just want to try to install the snappy image on to USB drive and boot from there.

---

### Post by ventrical on 2015-07-07
Code how to boot with kvm:

```

dale@ventrical-MS-7798:~/Downloads$ kvm -m 512 -redir :8090::80 -redir :8022::22 ubuntu-15.04-snappy-amd64+generic.img

```

Notice the directory.

Regards..

---

### Post by grahammechanical on 2015-07-09
There a 3 snappy-core channels - stable, edge & rc, which = release candidate.

The images all have the same file name. Which makes it difficult to have more than one snappy-core image. Unless we move each downloaded image into its own folder and then from that folder unpack the image and then launch the image in qemu from the folder as well.

But we still cannot have more than one version of snappy-core running in qemu. If we try we get this error

> qemu-system-x86_64: could not set up host forwarding rule ':8022::22'
qemu-system-x86_64: Device 'user' could not be initialized


At the moment the images from the rc channel seem to be the same as the images from the edge channel. At least snappy info says:

> release: ubuntu-core/15.04/edge

For both images.

Regards

---

### Post by ventrical on 2015-07-09
I'm using the /stable/ (shame on me ) :) on both kvm and standalone bootable image.

 Just on a side note...you can change the -m option to 1024 and then just put in the name of any image or .iso and it will run in qemu.

-m = memory

ie;

```

dale@ventrical-MS-7798:~/Downloads$ kvm -m 1024 wily-desktop-amd64.iso

```

regards..

---

### Post by ventrical on 2015-07-09
> **grahammechanical said:**
> There a 3 snappy-core channels - stable, edge & rc, which = release candidate.

The images all have the same file name. Which makes it difficult to have more than one snappy-core image. Unless we move each downloaded image into its own folder and then from that folder unpack the image and then launch the image in qemu from the folder as well.

But we still cannot have more than one version of snappy-core running in qemu. If we try we get this error


Regards

I think though with  the Docker framework you can create a container and import an image into it.. at least this is what I think it can do.

```


sudo snappy install docker

```

then just run docker --help and you will see all the options.

regards..

---

### Post by ventrical on 2016-01-31
Good news. Here is the e-mail Mark has sent me. Looks as if  snappy_snappy personal has changed hands over to Will Cooke. The good news is that Mark is keen on getting this program going asap. Bravo..

> 

Mark Shuttleworth                                                                                                                                         
                                                                                                          12:23 AM                                                      
                                                                                                          [      [IMG]https://blu185.mail.live.com/ol/clear.gif[/IMG]    ]("https://blu185.mail.live.com/ol/#")                     
                            
                                                                                                                                                                                                                                          To:  Dale Beaudoin, Will Cooke                                                    

                                              
                          
                                      [URL="https://blu185.mail.live.com/ol/#"][IMG]https://a.gfx.ms/ic/bluemanmxl.png[/IMG]

[/URL]


                                                                                      
                          
                        Hi Dale
 
I think Will Cooke is the person responsible for this, and I too am keen
to get a proper snappy desktop into testing asap.
 
Mark
 
On 30/01/16 22:11, Dale Beaudoin wrote:
> Hello Mark,
>
>
 I am inquiring about the current state of snappy_personal desktop 
images for x86/amd64 desktop devices. I , along with a few others at 
Ubuntu Development Version Testing,  have been early adopters trying to 
test the images on various desktop frameworks. About a month ago the 
images stopped updating. They were  called <personal_x86.img> 
which  had Unity8+mir on top of snappy_core. 
>
> My 
question is: Will there be more snappy_desktop_personal images coming 
out in the near future or will we have to wait until the next cycle?
>
>
 I am current admin for Ubuntu Development  Version Testing and I would 
like to share with other early adopters your take on this matter.
>
> Thank you.
>
> Regards..




Edit: I will try and contact Will Cooke.

@grahammechanical

If you want to try and contact Will Cooke on this .. please do so.

Thanks..

Regards..

---

### Post by ventrical on 2016-01-31
I e-mailed Will Cooke , Ubuntu-Desktop-Manager, through launchpad and inquired as to  current and future status of snappy_personal.

I will let all know when and if I recieve a reply.

Regards..

---

### Post by QDR06VV9 on 2016-01-31
That's Great thanks..
Stay Tuned: same bat channel, same bat time...:D

---

### Post by ventrical on 2016-01-31
hehaheha  kewl:)

+1
da da-da da-da da-da da! .. hehe

---

### Post by ventrical on 2016-02-01
@cariboo or other mod

Could we close this thread please. Snappy personal image testing will not start until next cycle (16.10) and I have already opened another thread on this.

Thanks..
Regards..

---

### Post by slickymaster on 2016-02-01
Closed per OP request.

---

### Post by cariboo on 2016-02-01
Thread closed by request.

---

