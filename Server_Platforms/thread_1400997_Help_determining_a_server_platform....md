---
title: "Help determining a server platform?..."
date: 2010-02-07
forum: Server Platforms
---

### Post by VcDeveloper on 2010-02-07
I'm kinda getting brain freeze reading a lot of documents regarding server set-up and administrations to the point that it is gotten more confusing then clear.

I want to set-up and Bazaar Version Control Server for my developers to checkout/in projects.  I want it password based, each developer has to have a certified certificate to access the server, so I would like to have a CA on the server, be able to access the server from home.

I've partially read about OpenSSH, OpenLDAP, eBox, Apache SVN and so on and so forth.  I would appreciate is so much if any guru server administrators of any level help me out on this.  I'm confused on which direction to take.

I install one way, then install software that I hope would help, but then find out the authors don't include complete (if any) documentation, incomplete tutorials or the software doesn't work like it should.  Then I have to be patient and wait for a reply to my help.  This takes days and some times weeks or never at all.  I go to these authors LaunchPad sites and to many are nowhere to be seen.

Ubuntu, you should have a strict guideline on these so called developers or teams and not allow them to publish software for your system unless it is completely functional and contains complete documentation that a dummy, newbe or a amateur can understand.  I'm a experience software developer 20+ years and I can't even follow most documentation put out by these developers.

I'm so happy I can virtualize everything or I would be so frustrated with this field or I would quit and go work for Mc Donanld's because making hamburgers is much more simpler than following most of the documents being handed out.

Ubuntu is an excellent Linux OS, but it's some or most of the software that is available for it is causing me to be frustrated.  openSuse is another excellent Linux OS I worked on for a while.But,   professionally speaking, if you two Linux OS got together there would be no other Linux OS on the planet that would be in the same league.   

Seems like when I went from one to the other I end up sacrificing major features, performance, ease of us with the OS and software packages to frustrating use, professional done front-end to a ugly one and so on.

I'm staying with Ubuntu, because some of the major things attracted me is it's professional done front-end, notification interface, style, overall core applications.  But, some or most of the third party software...., Argh! Well, they don't uphold the same professional quality as Ubuntu's core functionality and it needs to be fixed.  

My confidence in them is almost nill and I can count on one hand on a few software I can depend on and it's not helping me to accomplish my overall goal.  One is the Version Control Server using Bazaar among others.

So, can anyone help me get started in the right direction for this project?

---

### Post by gombadi on 2010-02-07
Selective quoting -

> 
I've partially read about OpenSSH, OpenLDAP, eBox, Apache SVN and so on and so forth.

Ubuntu, you should have a strict guideline on these so called developers or teams and not allow them to publish software for your system unless it is completely functional and contains complete documentation that a dummy, newbe or a amateur can understand

I'm staying with Ubuntu, because some of the major things attracted me is it's professional done front-end, notification interface, style, overall core applications. But, some or most of the third party software...., Argh! Well, they don't uphold the same professional quality as Ubuntu's core functionality and it needs to be fixed.


May I suggest you do some reading on open source/Free Software, the ideas behind it and what to expect from it.

Ubuntu is a distribution that takes software from many different open source projects and combines it into the Ubuntu distribution. As such it is very difficult to set guidelines for these projects and expect the project to follow them. If Ubuntu refused to include projects that did not meet guidelines in documentation that a noob could understand then there would not be many packages in Ubuntu.

I think you will also find that the vast majority of packages included in Ubuntu are third party - Gnome desktop, Firefox, Thunderbird, Linux Kernel, Perl etc

For your requirements can I suggest that you break down the tasks you are trying to do - i.e. How do I configure ssh to allow secure password less entry, how do I configure a version control system securely. That way people will be able to assist you in that smaller tasks that go together to get your system up and running. It is easier than trying to grasp the whole project at once.

BTW - If you have spare time then I am sure some of the projects you had trouble with would welcome some documentation from you that would help others to use their software.

---

