---
title: "Need Help Setting Up Startup Business Ubuntu Machines"
date: 2018-02-05
forum: Ubuntu, Linux and OS Chat
---

### Post by farukhkhan21 on 2018-02-05
Hello Guys,


Recently I have been working on a startup e-commerce business. And I want to power every machine at my workplace with ubuntu on it. For my office staffs such as developers, product managers, support assistants, accountants and admins I am planning to provide some low end Intel and ARM computers and laptops to just get the job done properly.

So, basically I am trying to make some customized ubuntu desktop versions which will run on both arm and intel for all my different departments.

For Example:
1. Developers Ubuntu will go with it's own pre-defined software packages only. Nothing extra. Such as: Latest Atom, Git, Firefox etc. All the other extra packages that comes with ubuntu desktop should not be in the os image. Making the image more optimized with small footprint. But with this process I don't want to break anything related to Ubuntu Base/Core which makes the OS secure and stable. Also, some custom built softwares for my company and from other repos will be pre-installed.

2. Product Managers Ubuntu will have LibreOffice and some other pre-defined packages only.

etc.


Is it possible to put some kind of network installer on every ARM or Intel pc sd cards or eMMC or SSD? While booted it will ask for "Which department OS I want to install?" And the installer will check for some config files in my local server accordingly for different departments defining all the packages needed to be installed and all the settings and configurations needed to be done for that particular department? And maybe take the original Ubuntu Desktop ISO from my local server for fast installation?


Most importantly I don't want to break anything which makes an Ubuntu OS ubuntu. I want to keep it original with it's robust security and stability. Just I want to pre-define some softwares and configurations. Any help would be really appreciated.



Thanks in advance...

---

### Post by QIII on 2018-02-05
Hello!

What you are asking about is not specifically an Ubuntu issue, but a Sys Admin's job.  There are a lot of tools out there (Ansible, Puppet, etc) used for this type of thing.  But they don't work with a casual wave of a wand.

Your needs require a person, specifically one trained as a Sys Admin.

---

### Post by farukhkhan21 on 2018-02-05
Actually I am not planning to use any unofficial tool for doing this. Just now I checked Ansible and Puppet and it seems like they are software lifecylce automation software. Good tools but I am thinking of doing this in the official ubuntu netinstaller. Is there no way to configure this netinstaller to suite my needs? And after all my company budget at this moment cannot afford a SysAdmin for this thing.

---

### Post by farukhkhan21 on 2018-02-05
I have gathered some information about Ansible. It is really a cool system but I am wondering if this will clash with kubernetes which I am planning to use in my server cluster for gitlab CI.

---

### Post by QIII on 2018-02-05
If you download the source code for the installer and can re-write it to suit your needs, you can make it do what you want and also prepare your coffee to order.  :)  That would be a good deal more work than you are probably interested in doing, though.

Without an admin, the best you can do is use the minimal installer -- perhaps as a net install -- to get just the very basics, add your choice of desktop environment, and then go through the very tedious process of setting up at least on machine in a particular group, create an image from that and install that -- perhaps as a net install -- on all the other machines that need identical provisioning.  Then you would have to do the same for the next department, etc.  Unfortunately, Canonical Ltd. is a very small company and does not employ enough developers to create an installer with the fine-grained level of complexity you need for a specially tailored enterprise.

You might find some fairly intuitive tools for doing this on something like AWS, but that would surely be expensive, too.

I'm not trying to put you off or be obtuse.  This sort of thing is exactly why Sys Admins, System Engineers and DevOps arrangements exist -- otherwise you'd need a supercomputer to bring to bear the AI needed.  Even then, you'd have to be able to tell the supercomputer what you wanted in a way that it could understand.  Humans are much easier to have that dialog with and they are far cheaper than supercomputer time.  A Sys Admin can take notes, ask questions, get your wishes in order and sit in a central location to write scripts, playbooks or whatever, push the configurations to targeted machines, test, take user input, re-configure again, test, take user input ...

The short answer is "No, it is extremely unlikely that you will find an open-source tool that will take your complex conditions and automatically configure your entire enterprise."  This does not apply to Ubuntu only, but to every OS and every distinct enterprise.

---

### Post by mastablasta on 2018-02-06
> **farukhkhan21 said:**
> . For my office staffs such as developers, product managers, support assistants, accountants and admins I am planning to provide some low end Intel and ARM computers and laptops to just get the job done properly.



give them crippled tools from the start? reduce their productivity? why? 

when i  started my work here i got a crappy PC. then i had to do backorders. the PC processed them for 1 hour to spit out the list. it used 100 % CPU for that. so my productivity was i ran the command and then i could go around a bit doing nothing. or just sit there and sms what was at the time my girlfriend.  now i have a proper PC. backorders are processed in background and i no longer have time to look around. i earn the company a lot more and all i needed was propper tools.

if you are on a budget get descent older/used desktops or laptops from other companies and install the full OS. if you are serious - get them proper tools so they can do their work the best they can. devs will need strong CPU and plenty RAM, office and support staff will do well with some i3 or similar. maybe even a recent Pentium will do with enough ram, so they do not need to wait for staff being processed. 

if everyone does not have the same tools how will they exchange information efficiently?

---

### Post by farukhkhan21 on 2018-02-06
Hey mastablasta, I totally understand your concern. But I think you misunderstood me there. I am not stripping down any toolset. I will provide the developers with whatever tools they will need for working on my e-commerce site. I won't compromise on the tools. Also if they needed something else extra to ease up some work I will also provide them. And the hardware I am planning for the developers is also high end ARMS. But it is ARM. Also, planning 2nd hand Intel Core i3. That's why I want to keep the OS as optimized as possible to reduce the extra os applications overhead so that they get the best performance out of it. Suppose a developer doesn't need GIMP for instance. Also, not all the games that comes with Official Ubuntu Desktop. And there's other packages like this.

And @Qlll, I understood what you said. I am trying to grasp the concept of Ansible and puppet with some documentation reading. But I think, I will give the modifying ubuntu netinstall source code approach a try. But I have no idea where ubuntu stores it's LTS and Stable channel netinstaller source code. And is there any pre-documented compiling method for the available source codes?

Another concept I am not able to understand is the difference between netinstaller and the Minimal ubuntu CD/ISO. What are the main differences between these two ISO packages?

---

### Post by mastablasta on 2018-02-06
> **farukhkhan21 said:**
> Hey mastablasta, I totally understand your concern. But I think you misunderstood me there. I am not stripping down any toolset. I will provide the developers with whatever tools they will need for working on my e-commerce site. I won't compromise on the tools. Also if they needed something else extra to ease up some work I will also provide them. And the hardware I am planning for the developers is also high end ARMS. But it is ARM. Also, planning 2nd hand Intel Core i3. 

Still not sure why you would use ARM?! do you plan to sell ARM based  applications or something? it's better to have good PC and then use virtualization. you will need to compile applications for ARm. you might later need something or want something you now do not know you will need yet. then what? compile it all yourself? maintain it yourself? to me it is ridiculous. plus compiling code requires CPU power.

> 
That's why I want to keep the OS as optimized as possible to reduce the extra os applications overhead so that they get the best performance out of it. Suppose a developer doesn't need GIMP for instance. Also, not all the games that comes with Official Ubuntu Desktop. And there's other packages like this.

the disk space lost to such apps is minimal. i mean in the time when disk space is cheap and measured in TB what does 300 MB more or less mean to you? you can still install basic OS, remove some apps you don't want and then create your own distro using something like Linux Respin. then you you use something like Ubuntu oem installer or some other better method to deploy same OS across the hardware (if you do not use ARM at all). then you have various system admin tool that can install additional software on clients that might need it. it would work that developer would want for example Atom and you would install it for them. Ubuntu offers Landscape for that. i think it is free for 10 machines. You could then just use stock image and uninstall certain apps from everyone. 

bottom line - unless this is some larger firm with 100 or more employees you are over complicating things. if you expect to scale up, then buy equipment that supports that.

> 
Another concept I am not able to understand is the difference between netinstaller and the Minimal ubuntu CD/ISO. What are the main differences between these two ISO packages?

i think they are one and the same. netinstaller means oyu onyl get to install barebones OS. just about enough to boot the PC. everything else has to be added later on manually. including desktop manager and such. i would not advise it unless you know what you are doing or are prepared to study a bit on what you actually need.

note that there is no point in using net installer and then installing Ubuntu desktop to it. in that case you might as well just install Ubuntu from the start.
however, using netinstaller and then adding for example xfce4 will give you barebones OS. you will still need to add some apps to make it fully functional but it will be super light and "clean".

i would suggest since, you asked for advice, to give a bit more information. number of people (clients), hardware budget, what kind of developing they will do (website, PHP etc.?), server ? will there be soem test server? will security be handled inhouse? backups?...

---

### Post by farukhkhan21 on 2018-02-06
For ease of understanding I will provide my full plan here. But before that let me provide my background. I myself is a professional software and web developer. I have almost 5 years of experience with programming languages like C, C++, C#, VB, HTML, PHP, SQL etc. I have been a network admin for an oil company in my country for about a year. So, I have experience with mikrotik and some little bit knowledge of cisco. Also during my network administration on the company I managed some of their linux servers also. But it was long time ago and they really didn't had any automation or scalability on their servers. It was basic old school setup. I myself used linux in many cases. Sometimes for hosting game servers, for compiling my softwares, for managing cpanel whm servers and also some automated bash scripting. I am always keeping myself up to date with modern technologies such as CI, CD, kubernetes cluster, load balancing, reverse proxy, docker, ansible etc.


My Budget: $1500-$2000 for all the tech setups in the office. My company is a low budget startup because there are various risk factors that is needed to be calculated before increasing the budget. We have total three partners in the company and the company is basically based on Bangladesh. But I am living in Malaysia and in the future I will trying to expand the business in here as well. 5-7 Developers. 3 Product Managers, 5 Support Assistants, 3 Marketing, 3 Admins, 4 Data Entry, total around 25 staffs initially and will be increasing. These 17 machines will be a combination of both desktops(big screen) and laptops(13" or 15"). Mostly the development work will be web based applications and in little often some desktop applications powered by C, C++, JAVA and Electron. All these applications will be developed under docker without thinking about the platform dependencies. Well, docker don't usually care what the platform is.

My Plan:
1. I will configure 4 digitalocean standard droplets as the production server. $5/mo each with configuration of 1GB RAM, 1vCPU, 1TB BW and 25GB SSD. I will go for a Load Balancer -> appserver1, appserver2 -> MySQL Database server configuration. This will run opencart application for my e-commerce. DigitalOcean provides their own load balancer system with unlimited bandwidth but that costs $20/mo. As I won't be needing that much of bandwidth for now I am using a $5 server as the load balancers. NginX will be the webserver and I want to include a simple mail server also in the appservers. Then gradually according to my website traffic and needs I will scale deploy more appserver nodes in different regions if necessary. Also, I will upgrade the MySQL server as necessary. Later if needed I will deploy more than one database server for clustering. And all this things I want to do using kubernetes and docker. So, that if I want to deploy more than just opencart in my appservers I have the option to simply create a docker image and deploy using kubernetes. I don't need to track which app is running in which appserver. Kubernetes will handle that for me. And also to scale up or deploy more servers I am planning to use the digitalocean API. This is my whole website cloud setup that I have been planning. Cheap and Scalable.

2. Now in my office I am planning to setup a small ARM cloud. Which will include a test server, master server, application server and lastly a backup server. Now let me state all the functions of each servers and their configuration.

Test Server: ARM 32bit. 10 Nodes Cluster. 10 Cores@1GHz = Total 10GHz Clock Speed of the cluster, 512MB@10 Nodes = Total 5GB Physical RAM. I will create Swap for another 5GB RAM. So, total 10GB theoretical RAM. Storage around 50GB free after OS and Swaps. Now, this test server will be controlled by the master server. In the application server there will be GitLab installed and all the developers will use that gitlab for their all developments. And when they will do some pull requests on the gitlab the gitlab will manage it through a pipeline cycle of test -> dev -> production. For test and dev cycles the gitlab will automatically create docker containers with the code to be tested and then auto dispose when the test is done. Also the dev codes will be containerized and run on the test server and get dispose after the gitlab production is pushed to my digitalocean production servers. This will happen for any web based docker supported apps that my development team will work on using gitlab.

Application Sever: Three ARM 32bit. 3 Nodes Cluster. 12 Cores@1.8GHz = Total 21.5GHz Clock Speed, 2GB@3 Nodes = Total 6GB Physical RAM. Swap another 6GB so total 12GB theoretical RAM. Maybe I will run gitlab CE here or in gitlab.com, not sure about that yet. A teamspeak server will also run in this cluster. And any other mysql databases and server softwares that are needed for inventory management and other company related tasks. All the deployments will be docker and will get controlled by kubernetes. This is also one sort of production server but this one is my local prod server. Any verified app from the test server can get deployed in this server also. Maybe it will also have a 50GB SSD for low latency applications.

Backup Server / Storage Server: One ARM 64bit, 1 Node. 1.5GHz@4 Cores = Total 6GHz Clock Speed, 1GB RAM and 2GB Swap. Total 3GB theoretical. Three 128GB SSD in RAID2 configuration for Data Integrity and Speed. And one 3TB HDD for nightly backups. All disks accessible using owncloud where all the staffs will have their personal storages of 5GB and work storage of another 5GB total 10GB. Another purpose of this server is to basically create or pull files and database backups from my digitalocean nodes for around 5 times daily and then push the data to the SSD drives and achieve in the HDD. All the data backups will be managed by this server.

Monitor Server: Haven't decided the specifications yet but want to go for ARM 64bit. This server is the master controller 1 Node server. This server will decide what the test servers will be doing now, what the production server will run, what applications will be running in the app server and how many backups the backup server will take etc. The master controller of kubernetes. Also, this server I want to use for the ubuntu software configurations and maybe some sort of system login for my staffs.

3. Last but not the least all the staff computers running Ubuntu will keep a connection with the monitor server with different permission levels. Maybe the developers can tell the monitor server to deploy a custom docker container. But the accountants cannot do that. The accountants may be able to query for some resource to cost logs from the monitor server etc. And the ubuntu installer will take it's configuration from the monitor master server what packages to install for developer, for product manages. And maybe push auto updates too when the staff's system is idle.

That's it. All networked using a MikroTik which will act as DNS, DHCP and Firewall.

Please suggest me anywhere I can improve my infrastructure by still being inside the company tech budget. I want my developers to use all the modern tools and deliver products in a fast pace. I have planned this keeping in mind both productivity and budget. Suggest me if you guys know any person or place from where I can get 2nd hand Intel based systems at cheap rate. But I won't put any crappy, rusty and dusty machines in my office environment. I want to keep the overall office slick looking for sending good message to the outside market. Please suggest me whatever products you think I should buy and also any other softwares like Ansible I should use to easily achieve my goal.

Some of the products I have been researching on:
[https://www.amazon.com/x5-Z8350-Processor-1000Mbps-Fanless-Computer/dp/B072WNWRHQ](https://www.amazon.com/x5-Z8350-Processor-1000Mbps-Fanless-Computer/dp/B072WNWRHQ)
[https://www.kickstarter.com/projects/udoo/udoo-x86-the-most-powerful-maker-board-ever](https://www.kickstarter.com/projects/udoo/udoo-x86-the-most-powerful-maker-board-ever)
[https://www.kickstarter.com/projects/jidetech/remix-mini-the-worlds-first-true-android-pc](https://www.kickstarter.com/projects/jidetech/remix-mini-the-worlds-first-true-android-pc)
[https://www.amazon.com/x5-Z8350-Fanless-Desktop-Computer-Bluetooth/dp/B076D5JJXT](https://www.amazon.com/x5-Z8350-Fanless-Desktop-Computer-Bluetooth/dp/B076D5JJXT)
[https://www.amazon.com/Mini-Supprot-Windows-Dual-Band-Bluetooth/dp/B0771CL954](https://www.amazon.com/Mini-Supprot-Windows-Dual-Band-Bluetooth/dp/B0771CL954)

And for the ubuntu distribution I want to keep it as clean and slick as possible. Not really planning to use Ubuntu Desktop Environment. I just want the core OS to be ubuntu due to it's robust security, stability and versatility. I have prepared a small list of the packages the developer will need initially. And for different departments the list of softwares will be different.
Developer Department: Atom, SourceTree, Git, Shutter, WireShark, Java, Chrome, Firefox, NoMachine and lastly some basic notes, reminders, calculator, clock, calender, owncloud client etc. No other packages will be needed for the developers aside this because they will be compiling and continuously testing their apps in the test server through gitlab CI. And I will manage the infrastructure from a remote place if some problem occurs.



Damn this reply got so long. Anyways, please try to help me out in any way possible. Never hesitate to provide your feedbacks and suggestions. Thanks.

---

### Post by QIII on 2018-02-06
@farukhkhan21:

What you are asking for is far, far beyond the scope of a forum like the Ubuntu Forums.  What you are asking for is the design and execution of a small but moderately complex IT infrastructure for a commercial enterprise.  While the UF might be an appropriate venue for questions about some small details that aren't working or are confusing, the scope of what you are asking for is not.  The UF does not exist to provide free infrastructure planning and execution for a commercial organization.

I understand your budget constraints.  But these things cannot be conjured from thin air, nor can they be executed as the product of a thread on an online forum.  The reality you face is that what you want requires an on-site Linux System Engineer, whom you might be able to engage under short-term contract.  After the initial setup, it may be necessary to engage a more long term, if part-time, Sys Admin to keep it running.  mastablasta has brought up a few things that you have not considered -- things that will require a human's dedicated attention.

I don't know the economic environment you may be facing in your locale, but I can tell you that in the US, I would not take on a project like this unless I were convinced that I would be able to make a tidy profit.  That is the nature of my business.  I don't do what I do gratis or pro bono.

I think you are being extremely unfair and unrealistic to expect the volunteers (including the Staff) here to do this sort of work for you at no charge.  If you can't afford what you need, then you should pursue GoFundMe or a similar source of funding.

This is the world as it is.

---

### Post by Frogs Hair on 2018-02-06
> What you are asking for is far, far beyond the scope of a forum like the Ubuntu Forums.

Closed for reason stated.

---

