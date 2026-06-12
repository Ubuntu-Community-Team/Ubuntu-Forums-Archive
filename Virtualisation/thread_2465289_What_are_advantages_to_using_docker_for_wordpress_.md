---
title: "What are advantages to using docker for wordpress in ubuntu?"
date: 2021-07-28
forum: Virtualisation
---

### Post by diosmioesricardo on 2021-07-28
I want to install Wordpress but was advised to use docker.  What are advantages because it's a little more complicated for me.  Does it provide better compatibility with uploading my site to my web host?

---

### Post by TheFu on 2021-07-28
Containers aren't the same as virtualization. They are very, very, different.

---

### Post by MAFoElffen on 2021-07-29
I agree with TheFu totally on this. He can probably get in to more details on that. I've only started working with installing Docker and using Docker containers since 2014 or 2015...

No one else answered this and there is more to it that probably needs to be explained...

There similarity between the two is that they are virtualized. 

If you are looking to get up quickly, have a small learning curve and have persistent changes easily. and have the ability to test whatever you do on difference OS'es Kernels, and releases, then a VM host is ideal. If you are looking to run applications on the same OS and Version of Kernel,shared by diffrering applications, then Docker is ideal... 

But there is some drawbacks to doinng things on Docker also. It has a bigger learning curve, having to do lot of that to learn how to redeploy what you have done, and to have any kind of persistence for your data... 
> By default all files created inside a container are stored on a writable container layer. This means that: The **data doesn't persist when that container no longer exists**, and it can be difficult to get the data out of the container if another process needs it.
Just dealing with the data, with whatever you database choose, it needs to be persistent (This is just one issue, and extra work to do)
> By default all files created inside a container are stored on a writable container layer. This means that:
  
[LIST]
[*]The data doesn&#8217;t persist when that container no longer exists, and it can be difficult to get the data out of the container if another process needs it. 
[*]A container&#8217;s writable layer is tightly coupled to the host machine where the container is running. You can&#8217;t easily move the data somewhere else. 
[*]Writing into a container&#8217;s writable layer requires a [storage driver]("https://docs.docker.com/storage/storagedriver/") to manage the filesystem. The storage driver provides a union filesystem, using the Linux kernel. This extra abstraction reduces performance as compared to using *data volumes*, which write directly to the host filesystem. 
[/LIST]
  Docker has two options for containers to store files in the host machine, so that the files are persisted even after the container stops: *volumes*, and *bind mounts*. If you&#8217;re running Docker on Linux you can also use a *tmpfs mount*. If you&#8217;re running Docker on Windows you can also use a *named pipe*.


Then there is the subject of the 3-4 Docker application containers needed to run a WoordPress Site + the Docker Volume Mount, the configuration of each,and the hard-wiring to all... To replicate that for redevelopment, usually using scripts... or an Ansible playbook, and a container orchestration tool such as Docker Swarm or Kubernetes. Sound simple? A bit of a learning curve.


Virtual Machines versus Containers is subject. Each has pro's and con's and are dependent on what needs to be done.

Virtual Machines are easy for people to setup and maintain. There are many companies out there with with pre-built WordPress VM's... That say say are transportable to the cloud... Which is funny, because most of those VM's are for VirtualBox and VMplayer... Which if you did it on KVM, then those VM's are seamlessly transportable to Cloud based Environments, which a lot of them are KVM based. You don't need much to run WordPress.

For a VM, everything runs and is persistent within the same VM. Whatever you do, is just there.

The funny thing about Host and Guest system requirements for both of those, is just strange. Because the recommends for WordPress, for the Host and Guest seem to be the same, no matter if Docker or a VM.

---

### Post by TheFu on 2021-07-29
I don't use Docker for containers.  We decided to go a different direction for a number of complex reasons.
The vast majority of people outside business environments who deploy using docker containers seem to be non-admin people. That leads to problems. Sometimes tiny and sometimes being completely hacked.  The company behind Docker has a history of making claims that turned out to be false.  

Pre-built docker containers should only come from extremely trusted sources and the deployment team should expect to update their container weekly, at a minimum for wordpress.  The company behind wordpress, Automattic, is very trustworthy, but the rest of the ecosystem around it concerns me based on a long history of 1M hacked websites on the internet on any given day.  

To anyone thinking to put wordpress onto the internet who doesn't have admin skills **AND** 10 hrs of specialized docker training, I'd say they are better off using the free wordpress sites run by Automattic, or paying for wordpress hosting that also includes all patches for $20/month.

If the goal is to run Wordpress inside a private LAN, not connected to the internet, I'd say go for it. Learn.  While learning about WP, php, mariaDB, patching, and backups for the wordpress site for 6+ months.  For non-admin people, they will need to get their networking skills a little better just to access WP and have it access the DBMS.  That's a good thing, since network security is extremely important.

I haven't kept up with Docker container management the last 5 yrs after attending a hands on *Docker Best Practices* conference.  I found it enlightening as enterprise Linux companies had their docker gurus teaching.  The Docker-company (whatever they changed their name to be), wasn't at this conference, so I feel we got the straight poop on the great things and bad things around docker containers.  Clearly, they were pro-docker.  
The main take-away from that weekend was that linux containers are like paper airplanes.  
If a container isn't doing what you need, crumple it up and build a new container from scratch, then deploy it.
There is no patching, just rebuild a fresh container, then deploy that fresh container where ever it needs to run.  
Have one wrong setting inside the container?  Nuke it from orbit, rebuild a fresh container with the config file corrected, then deploy it.
The key part of this management is having a nuke, build + deploy process automated.  Anything less is a failure.

If you care about security, take a look at [https://sylabs.io/singularity/](https://sylabs.io/singularity/).  They next on my list to check out for container needs. It isn't the most popular.  I need to get off LXD containers.  Canonical's mandate to use snap packages for lxd has driven us away.

Just too many things on the to-do list to handle them all.  What's the saying?  "Perfect is the enemy of done."

---

### Post by scorp123 on 2021-07-30
> **MAFoElffen said:**
>   There similarity between the two is that they are visualized.

I'm pretty confident you mean ***"virtualized"*** ... because otherwise your sentence does not make any sense to me and you'd need to explain that (I'm not a native English speaker).

---

### Post by TheFu on 2021-07-30
Probably not.  Containers ARE NOT virtualized. There's no virtual hardware presented. No emulation of a CPU or NIC or anything else.  The kernel from the hostOS is used inside the Container.  Even userids inside containers are shifted from the host. No extra kernel modules can be loaded into the container. This isn't just docker. It is for all Linux Container tools - which there must be 20-50 options.

Containers are logically constrained using cgroups and chroot. This is closer to chroot+BSD jails than anything else. Some of the same attacks to break out of jails and chroots work against containers. 

The main protection for containers is to not have any other tools/programs inside the container except what is required to run the primary service.  If we have a web server inside a container and don't put any userland programs there too, it is next to impossible to break out.  If only nginx is there, no ls, bash, sh, csh, ksh, zsh, vi, nano, dd, df, du, cat, more, chmod, chown, sudo or any other commands, then the theory is that any attack can only run the program that was provided, as it was configured.  Since that's the entire point of the container - what's the risk? It can run only the 1 program, which is what we want.

In theory.

---

### Post by MAFoElffen on 2021-07-30
I meant "virtualized'. Maybe not in the specific technical nuts and bolts, but in that in the concept, that altogether, with the pieces it is using, whether it is shared or not, through the layers, it "is" a virtual instance... and not a physical machine. In the same conceptual scalability, whether we are talking about two physical machines doing distributed processing locally on the same network, or using cloud services, across the world.

English was not my first language growing up. But I think I have grasped it through the years... I mean no disrespect to anyone, though I have a lot in my head, and sometimes find it a challenge to explain that on the outside in words, to all levels of who might read it, at one time.

I do not speak for TheFu and he may think differently. TheFu and I have talked a bit on this previously. Even as recent as last night (LOL)... Different ways to do "virtualization"... whether that is at the kernel level, systemd.container, LXD, linux containers, chroot, application containers (not just Docker), Type 1 or Type 2 hypervisors... All of them are conceptually virtualization, "virtualized" and not psychical metal.

I think we can all agreed on that. Each happens at different levels. Each are their own animals. Each may have it's own place, and time. Some things change with time. Somethings are better and have a niche for something specific. Each one requires that you do things differently, based on what you are using. Each one requires that you do things to make them work...

Basically, without going into specific details, that's "the short answer". Agreed? And both I and TheFu seem to both agree that WordPress in a container is not a good idea. It can be done. It is possible. But it doesn't make sense for something long term. (And there's so much that we didn't bring up... that supports that, especially for someone just starting out...)

Here's my two cents on that beyond what I have said... If I think containers, as TheFu started to say, it's something where I see as you start an instance of, do a job or something specific, for a limited period of time until that job is over, then you end it's existence. Bang. Temporary existence. Full resources are there again. As he mentioned, if something is wrong with the container (application development or a setting), then you make changes, rebuild your template, redeploy... wash, rinse, repeat... I don't think of containers for something that should be there, up and running, 24x7, for years. That is just not common sense to me. 

For me, to me... that personal bias includes OS and applications containers. Maybe that's just me and that I'm getting old and things may have changed that change that, but I haven't seen that yet... Each does have it's place. No matter where that place may be...

---

### Post by diosmioesricardo on 2021-08-02
Ok, thanks to all for your replies.  I think I am going to skip docker and go with a Bitnami installation.  Much simpler for me and I don't want to complicate things.

---

### Post by TheFu on 2021-08-02
Is Bitnami trustworthy?

---

### Post by MAFoElffen on 2021-08-02
@TheFu: Yes and no.  Mostly No.
> [Bitnami]("http://bitnami.com") provides free all-in-one installers, virtual machines and cloud images for popular open source applications.
Bitnami got bought out by VMware... As applications package installations sorts of affairs... But their images and support for are mostly for on VMware and VirtualBox, then Cloud. As I remember (been awhile), the defaults for images were vmdk images. Still does not address anything about security. Just the application install and configuration of. And locks him into those two type 1 hypervsiors, unless he converts them for a Type 2 hypervisor images, besides VMware.

---

### Post by TheFu on 2021-08-02
I consider the "type-1/2" all marketing.  For me it is enterprise or desktop hypervisors, which generally speaks more about stability and performance vs some fancy GUI.

Converting from vmdk to anything isn't hard.  qemu-img can do it, right?

Besides getting a pre-made setup from a random place that I wouldn't trust, I still have the question about security and maintenance for Bitnami.  How easy is it to migrate from v1 ---> v2 of web-app XYZ?  When there is a huge security risk, like happens ever 2 weeks with wordpress, what is involved in patching so we don't have 2M hacked wordpress sights on the internet?

---

