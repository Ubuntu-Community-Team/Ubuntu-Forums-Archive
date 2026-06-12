---
title: "build system similar to cPanel, Plesk Panel etc."
date: 2015-06-21
forum: Server Platforms
---

### Post by piotr26 on 2015-06-21
I need to build system similar to cPanel, Plesk Panel etc.
Of course could i use one of them but in my case i need to integrate  whole process of creating websites with my companies CRM (based on PHP),  so i could automatic define new domains with template files based on  informations from CRM. For example, one of workers filling out the form  in CRM, that one of our client wish to have a website with specific  domain and template. Then the system grabs all this data and creating in  www directory, catalog named companyname.com, extracts template files,  and do server name job.  So the rest of the job is only buying domain  and pointing to my company server. I would prefer server based on Linux.

Which language / technologies is best to use in this case?
Maybe there are some ready solution which I can program easy in my way?

Thanks for help!

---

### Post by volkswagner on 2015-06-22
I'm not sure how much automation can be used, but have you checked out [ispConfig3]("http://www.ispconfig.org/page/home.html")?

---

### Post by TheFu on 2015-06-23
So, I've never done this and have barely even used anything like this myself. Basically, I'm clueless, but that has never stopped me before ... 

In the old days, whenever I needed some tool like this, I'd visit freshmeat.net to see what was available in the F/LOSS solutions - watch the licensing if this is used in a business. They changed the name of that site - seems "freshmeat" was being caught by pron filters - it is completely safe for work and children. Think the new name is "freecode".

There is another how-to website ... howtoforge.something.  With every new distro, they make a "Perfect Server" Guide - which shows how ISPs setup servers for web, email, ftp, hosting.  Falco is reputable, but don't always trust these systems are 100% secure.

If you are building your own - the best language is probably the language you know provided it isn't something like Java, C, C++, C#, R.  Python, Perl, Ruby would be in my short list for consideration.  

Also, it might be better to leverage a DevOps tool like Ansible, Chef, Puppet, SaltStack, Rexify for things like this.  Support by ISPs to end-users gets expensive when they give login authority to the users.  With a DevOps tool, you could see what the end-user had changed with 1 command - or just put everything back to the defaults and be done.  Ansible/Salt are "push" tools.  Puppet/Chef are "pull" tools - be aware.

If I were given this task and we couldn't find anything close, I'd build something that created Ansible playbooks based on some input from the CRM data.  In that way, I wouldn't need to re-invent the wheel AND wouldn't fall into the trap of having to build so many things that are already part of Ansible.  Ansible uses YAML as an input, which is both machine and human readable.  The playbook creation would be pretty trivial for a CRM input to create. Each of the sub-parts would be based on human-created "Roles" and "Tasks."  Each is relatively tiny, but very powerful. [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) has examples.

You didn't mention at which point containers or virtualization comes into this solution. That is something else for consideration. For a webhost these days, I would think that openstack would be a "given" - there really isn't any other viable option that is cost effective.

I would NOT use php - due to all the warnings from the OSWAP guys about php.

Anyway - hopefully my ignorance isn't too distracting.

---

### Post by mastablasta on 2015-06-23
why not use source code from existing projects (something like zpanel or similar)

---

