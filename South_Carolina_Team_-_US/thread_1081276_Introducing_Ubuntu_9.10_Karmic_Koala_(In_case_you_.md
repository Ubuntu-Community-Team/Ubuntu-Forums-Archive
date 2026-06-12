---
title: "Introducing Ubuntu 9.10: Karmic Koala (In case you missed it)"
date: 2009-02-26
forum: South Carolina Team - US
---

### Post by xarquid on 2009-02-26
(And some people may have had problems spelling "Jaunty Jackalope!" Hehe!)

>     

Ladies and gentlemen, allow me to introduce the Karmic Koala, the newest member of our alliterative menagerie.

    When you are looking for inspiration beyond the looming Jaunty feature freeze, I hope you’ll think of the Koala, our official mascot for Ubuntu 9.10. And if you’ll bear with me for a minute I’ll set the scene for what we hope to achieve in that time.

Server

    A good Koala knows how to see the wood for the trees, even when her head is in the clouds. Ubuntu aims to keep free software at the forefront of cloud computing by embracing the API’s of Amazon EC2, and making it easy for anybody to setup their own cloud using entirely open tools. We’re currently in beta with official Ubuntu base AMI’s for use on Amazon EC2. During the Karmic cycle we want to make it easy to deploy applications into the cloud, with ready-to-run appliances or by quickly assembling a custom image. Ubuntu-vmbuilder makes it easy to create a custom AMI today, but a portfolio of standard image profiles will allow easier collaboration between people doing similar things on EC2. Wouldn’t it be apt for Ubuntu to make the Amazon jungle as easy to navigate as, say, APT?

    What if you want to build an EC2-style cloud of your own? Of all the trees in the wood, a Koala’s favourite leaf is Eucalyptus. The Eucalyptus project, from UCSB, enables you to create an EC2-style cloud in your own data center, on your own hardware. It’s no coincidence that Eucalyptus has just been uploaded to universe and will be part of Jaunty - during the Karmic cycle we expect to make those clouds dance, with dynamically growing and shrinking resource allocations depending on your needs. A savvy Koala knows that the best way to conserve energy is to go to sleep, and these days even servers can suspend and resume, so imagine if we could make it possible to build a cloud computing facility that drops its energy use virtually to zero by napping in the midday heat, and waking up when there’s work to be done. No need to drink at the energy fountain when there’s nothing going on. If we get all of this right, our Koala will help take the edge off the bear market.

    If that sounds rather open and nebulous, then we’ve hit the sweet spot for cloud computing futurology. Let me invite you to join the server team at UDS in Barcelona, when they’ll be defining the exact set of features to ship in October.

Desktop

    First impressions count. We’re eagerly following the development of kernel mode setting, which promises a smooth and flicker-free startup. We’ll consider options like Red Hat’s Plymouth, for graphical boot on all the cards that support it. We made a splash years ago with Usplash, but it’s time to move to something newer and shinier. So the good news is, boot will be beautiful. The bad news is, you won’t have long to appreciate it! It only takes 35 days to make a whole Koala, so we think it should be possible to bring up a stylish desktop much faster. The goal for Jaunty on a netbook is 25 seconds, so let’s see how much faster we can get you all the way to a Koala desktop. We’re also hoping to deliver a new login experience that complements the graphical boot, and works well for small groups as well as very large installations.

    For those of you who can relate to Mini Me, or already have a Dell Mini, the Ubuntu Netbook Edition will be updated to include all the latest technology from Moblin, and tuned to work even better on screens that are vertically challenged. With millions of Linux netbooks out there, we have been learning and adapting usability to make the Koala cuddlier than ever. We also want to ensure that the Netbook Remix installs easily and works brilliantly on all the latest netbook hardware, so consider this a call for testing Ubuntu 9.04 if you’re the proud owner of one of these dainty items.

    The desktop will have a designer’s fingerprints all over it - we’re now beginning the serious push to a new look. Brown has served us well but the Koala is considering other options. Come to UDS for a preview of the whole new look.

UDS in Barcelona, 25-29 May

    As always, the Ubuntu Developer Summit will be jam-packed with ideas, innovations, guests and gurus. It’s a wombat and dingbat-free zone, so if you’re looking for high-intensity developer discussions, beautiful Barcelona will be the place to rest your opposable thumbs in May. It’s where the Ubuntu community, Canonical engineers and partners come together to discuss, debate and design the Karmic Koala. The event is the social and strategic highlight of each release cycle. Jono Bacon, the Ubuntu Community Manager has more details at [http://www.jonobacon.org/2009/02/19/announcing-the-karmic-koala-ubuntu-developer-summit/](http://www.jonobacon.org/2009/02/19/announcing-the-karmic-koala-ubuntu-developer-summit/) including sponsorship for heavily-contributing community members.

    More details of the Ubuntu Developer Summit can be found at [http://wiki.ubuntu.com/UDS](http://wiki.ubuntu.com/UDS).

    A newborn Koala spends about six months in the family before it heads off into the wild alone. Sounds about perfect for an Ubuntu release plan! I’m looking forward to seeing many of you in Barcelona, and before that, at a Jaunty release party. Till then, cheers.

Mark 


Link to original Mark Shuttleworth post: [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html)
Fridge post: [http://fridge.ubuntu.com/node/1831](http://fridge.ubuntu.com/node/1831)

---

### Post by alfu on 2010-01-01
Wow, cloud computing must be really great for some people, but you know what?  I think it would be just peachy to find an operating system that would:

1) Allow you to mark components for re-installation reliably (i.e., not wiping out the original one first before it discovered that the web-sourced replacement was unobtainium) so you didn't end up looking at the black screen of death two or three times a year.  Ubuntu doesn't: try marking the Network Manager for re-installation and just see what happens.

2) Provide a way for user data and system data to be segregated so user data could be easily backed up and restored in the event of system crash.  Ubuntu doesn't: it gives you permission denials whenever you try to copy most directories to backup media.

3) Run on non-proprietary hardware. Mac OS doesn't.

4) Not push a load of apps onto your HDD that you don't want, won't use and can't remove.  Micro$oft OSes don't.

Must humble users only wishing to use a computer to create content forever be forced to try to fly before they can even crawl reliably?

---

