---
title: "Sanity check please! SBS2003 and Ubuntu enviroment."
date: 2009-02-03
forum: Server Platforms
---

### Post by Poverty on 2009-02-03
I'm new to the Linux Server environment.  I've picked up the Apress Ubuntu book and quickly gone through it but what I want to do wasn't really covered.  So here's the scope of what I am trying to setup and I wanted to know if it is possible or if it should even be attempted.

Ok so I run a small business.  At the office I'm stuck with a lowly DSL connection.  I have SBS 2003 setup and everything is running ok.  I want to have my windows server host my email via Exchange and that's it.  Now I want to setup a LAMP environment at home on a cable connection to handle webserving, OS Commerce, Joomla etc.  

Now in my crazy brain I'm thinking all I need to do is plug in my domain records so that @ traffic goes to my office static IP and www or * traffic goes to my house static IP?  I also like Outlook web access functionality so I figured I could handle that with a sub-domain for the http access or something.

Will this work?  or am I setting myself up for failure here?  I know I've considered hosting and other scenarios but I don't mind tinkering and learning.  If this would work as an ok practice.

Thanks for any input you may have.

---

### Post by Thirtysixway on 2009-02-03
It could work.  I have my main domain pointing to my paid web hosting (handles allthe dns stuff) and added a CNAME that points to my home server.

---

