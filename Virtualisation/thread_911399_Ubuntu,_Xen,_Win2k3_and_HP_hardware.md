---
title: "Ubuntu, Xen, Win2k3 and HP hardware"
date: 2008-09-05
forum: Virtualisation
---

### Post by hooflung64 on 2008-09-05
Greetings,

I am about to engage in a major upgrade of our servers at work. The current PC is a Dell Poweredge 2600. We recently purchased another server for another task, a [HP Proliant ML150]("http://h10010.www1.hp.com/wwpc/hr/hr/sm/WF06b/15351-15351-241434-3328424-3328424-3580609-3670460.html") and we have decided to use this server to consolidate our websites for ourselves and our clients.

The caveat is that one of our new sites must be run on IIS with MSSQL. Moreover, the current websites are mainly 5 year old xml-asp(jscript)-mysq ran from IIS 6 which will need to be retained until I create a new website for that. The rest of our sites need PHP and Postgresql ( converting over from Mysql ) and I want each site to be its own virtual machine so separate clients don't mingle together in the config files. Thus we are going to Virtualize our servers. Huzzah!

Now I'm somewhat of a linux veteran. I love Ubuntu and use Debian Etch on my own personal VPS service. I've considered Gentoo as well but I just saw that the latest `ubuntu-xen-server` has 3.2 of Xen and that seems to be the sweet spot for Windows 2003 compatibility of non current Xen builds.

What I would like to know is :

Has anyone had any snafu's when undergoing this type of project?

Could anyone share their experiences with such moves?

Our server is certified to run with RH Enterprise 5 and thus, CentOS 5, so do you think Ubuntu Server 8.0.4 will have any hardware issues? 

Anyone have issues running MSSQL on top of Xen? 

Does anyone think KVM would be a better option?

We plan on updating the server to 8G of ram. Normally I'd jump all over using AMD64 builds as I do at home but would it be wise to just use X86 + PAE so I can run X86 guests or will Windows 2003 Win32 run fine as a guest on AMD64? 

I'll get a worklog going once we start digging into the conversion process next week.

Thanks for any help,
HF64

---

### Post by zehel on 2008-12-29
How have things gone for you?  I am also interested in implementing XEN on a few platforms, and am wondering how/if to do this.

---

