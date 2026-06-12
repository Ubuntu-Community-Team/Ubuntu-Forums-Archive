---
title: "Recommendations for Systems Management Tool"
date: 2018-10-30
forum: Server Platforms
---

### Post by computermichael on 2018-10-30
I am looking for a tool or tools to help manage a series of 100 Ubuntu Desktop 18.04.1 LTS deployments. Ideally I am looking for something that can handle remote control, patch management, software distribution, operating system deployment, network access protection and hardware and software inventory. Also allowing for management of Ubuntu Server deployments would also be helpful. I have heard of Ubuntu Landscape and Puppet. Will these two tools fit the bill?

---

### Post by slickymaster on 2018-10-30
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2018-10-30
If you can share your background with administration, we can tailor our answers better.  From the question, it seems you might be coming from a Windows background.  Only Windows needs special tools to do the things you are listing.  Every Unix-like OS can perform those things with some light scripting - except the installation of an OS on bare metal.  There are tools to accomplish that.

In the old days, DevOps was performed by creating scripts that used rsh.  Around 1995, rsh which doesn't have any encryption, was replaced by ssh. The great thing about these scripts was they were custom for the needs of the specific site. The bad thing was that every site had their own scripts, so it wasn't standardized.

In the early 2000s, some "fresh blood" got interested in Linux and decided to make DevOps an industry term, trying to connect a few different tools, usually sold with commercial support to that name.  Old-timers were doing "devops" for 40 yrs before that, but whatever.  Chef, CFEngine, Puppet and Salt were the most popular tools.   They all use an agent on all the systems to be managed and "pull" updates from the tool server.  Chef and Puppet also required the Ruby scripting language to be installed on every node. Ruby wasn't pre-installed on most Linux distros until 2016-ish.  Each of those tools had issues and complexities.  Opinions about each are around.  I looked carefully at Puppet and Chef, attending 1-day introduction training provided by the companies behind those tools.  After I attended those sessions and spoke with some people and heard about their problems using the tools, I was convinced the tools were worse than the problem they were trying to solved.  IMHO.

Then a Puppet engineer decided he could solve 80% of the problems with much less complexity and created a tool called Ansible.  Ansible uses ssh for the authentication (all your ssh infrastructure keys and certs work) and a "push" methodology to the systems to be managed.  It is built on python, which most distros have included since 2010.  Ansible is agent-less. Nothing except ssh needs to be setup on the remote systems. The other dependencies are already there for almost every distribution.

Salt-Stack, requires an agent, but scales to 100s of thousands of nodes to be controlled.  For me, requiring agents on each node was a non-starter.

So, remote control - which I don't know what you mean by that, but you can ssh into any system and have whatever access you need using ssh.  ssh is how every Unix-like OS is managed and most networking devices too, everywhere in the world.  Through ssh, you can patch, install software, setup firewalls, and gather any software/hardware inventory that you like.  I little scripting with a loop to log into every system on a subnet or by a list of hostnames and you've got automation.  I perform weekly patching for my 20 servers using a little bash script that has a loop, some server names, and a could apt-get commands which are run on each system.  It is about 15 lines.

Linux distros have software repositories.  You can setup your own and use the public ones together.  I have a caching setup so package updates are pulled by the first machine that requests it, but any other machines will get the local version first instead of pulling it from the internet again.

For bare metal deployment, there are a number of different tool.  I've never used any, but **Cobbler** was created by the Ansible team.  I bring up a new server about every 2 months, so it isn't a big deal.  All our servers are remotely managed - AFTER they are installed, but if you have proper server hardware with an iDRAC or IPMI facility, you just need a data center monkey to put in the flash drive or DVD so you can do the installation, then have them pull it later.

Hardware inventory - there are 50 tools for that, just depends on what you want.
Software inventory - there are 500 tools for that, just depends on what you want.

Ansible has something called "facts" which is software configuration and hardware inventory.  I just shove the output of lshw into a text file daily and include that in backups.  I also grab lvm and partition information while I'm at it and put those into some text files that get included in the system backups.  This way we have a record over time of any changes - intentional or due to failures.
```
~/backup# ls
blkid.txt   crontab.root  dpkg.list  lvdisplay.txt  vgdisplay.txt
crontab.thefu  df.txt        lshw.list  pvdisplay.txt
``` The other files I capture.

Really, once you are passed the point-n-click admin style, managing 5 or 500 servers really isn't any different or that much time, unless you have 500 snowflakes.  I have 20 snowflakes.

I don't know any businesses that use Landscape.  I've heard of many businesses using puppet or chef. I know a few that use salt, but smaller setups seem to choose ansible because it doesn't have magic locations and it uses ssh, which everyone has setup anyways already.  If you like, you can pay Ansible, but it isn't necessary. They have a pretty GUI that management-sorts seem to like called "Tower."  It was paid only until about a year ago. Redhat bought the Ansible company. The Ansible guy worked at Redhat for a few years ... I think he moved to Puppet Labs after that, but don't quote me.

I used Ansible for a few years early on, but as the tool was forced to become more comprehensive by clients, they had a problem breaking the old setups.  After about the 3 time, I decided I could script something faster and it would work for 20 yrs instead of 12 months.  I have admin scripts that still work today that I wrote in the 1990s.  They've been tweaked slightly, but not much over the years.

The main reason to use a formal devops tool is to leverage what other people have posted to github/gitlab online for trivial setups.  When you are new to Linux, those trivial setups are better than nothing, but once you become more advanced, you'll see all the little things the public scripts don't do in the way you know is better.

In the Unix world, we prefer tools that do 1 thing really well, not 1 tool that does 50 things "ok".   There is no need for something like SMS, for example.  The software distribution model was solved in the mid-1990s for most Linux distros.

If your boss says "we need a devops tool" and you don't want to be fired, then pick either puppet or chef.  IMHO, those are the "Microsoft" answer to devops. Many people like them and you'll never be unemployed.  You might hate going to work, but you will have a place to go, always.  Sorta like in the 1980s, nobody was fired for choosing IBM and in the 1990s nobody was fired for choosing Microsoft.

If you are running systems in a public cloud the answers are different than if you are running them inside a corporate data center.  Also, these days the default is to use virtual machines and containers, so the way that container are managed is totally different. None of these tools are used for container creation and rollout.  Where I am, we treat VMs just like we treat physical machines.

Anyway, hope these comments are helpful.  Every admin will have different views about this stuff, so don't think what I wrote is perfect for everyone or every situation.

---

### Post by computermichael on 2018-11-01
Thank you so much for the comprehensive response. I'm actually an undergraduate student trying to learn more about device management and wanted to see what professionals in the industry use so I can start gaining experience. I've had a hard time finding documentation and expertise online and wanted to see what would work best. I love working with Linux and want to see if you have any recommendations for what I should start with learning wise.

---

### Post by TheFu on 2018-11-01
> **computermichael said:**
> Thank you so much for the comprehensive response. I'm actually an undergraduate student trying to learn more about device management and wanted to see what professionals in the industry use so I can start gaining experience. I've had a hard time finding documentation and expertise online and wanted to see what would work best. I love working with Linux and want to see if you have any recommendations for what I should start with learning wise.

There is no "best" answer.  There is just what someone had to pick in the time they were allowed to choose.

Find a LUG - that's a Linux Users' Group.
Attend their meetings.
Listen.

Go to annual Linux Conferences. Come early. Help out the organizers. Stay late.  When the videos of the conference go up, watch the sessions you missed.

All the tools I listed have extensive documentation and videos online. So do most of the Linux conferences.

Device management tools are about 3rd year as a Linux Admin problems.  If you can't setup LVM in your sleep and use ssh perfectly, then concentrate on basic admin skills.  The tools don't replace that knowledge.  They just provide faster ways to screw up more systems when you don't know what you are doing.

If you want to learn Linux for administration reasons, work through all the LPI training for every Linux flavor you need to know.  That's probably Debian Server, Ubuntu Desktops, CentOS 6 and 7 servers.  [https://www.lpi.org/how-to-get-certified/free-training-materials](https://www.lpi.org/how-to-get-certified/free-training-materials) You can also work through the Redhat Training materials.  This knowledge is more useful in financial industries and corporations in North America than Debian.

Good luck and don't forget that this stuff should be fun.

---

