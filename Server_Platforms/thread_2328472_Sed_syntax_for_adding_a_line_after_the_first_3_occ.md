---
title: "Sed syntax for adding a line after the first 3 occurences of a line"
date: 2016-06-21
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2016-06-21
Looking to do a script to automate my server installation. I'm stuck on the cups config at /etc/cups/cupsd.conf

I need to add "Allow @LOCAL" on the next line after the first 3 occurences of "Order allow,deny"

I'm not sure if I need sed or what. I've debated just keeping a config file and copying it into place but would prefer to have it done inside of a script. Less to keep track of. Appreciate suggestions. Thanks

---

### Post by TheFu on 2016-06-21
*Any suggestions?*

As great as sed is, it isn't the best tool for something like this.  Take a look at ansible.  It is designed to manage systems and begins to make sense when you have 4 boxes up to 2,000 systems.  Plus you'd learn a highly marketable skill and be able to add "DevOps" to your resume. ;)

For something like this, I'd create a template and use the built-in j2 language to customize it as the template was pushed to the server running CUPS from the ansible workstation. For something like this, 20 min should get you up and working with Ansible.

BTW, back in the 1990s, we all wrote custom systems management script for stuff like this.  Tools like Ansible have just standardized all that stuff and brough reuse and best practices to the fight.

---

### Post by DuckHook on 2016-06-21
*Thread moved to **Server Platforms** as the more appropriate forum.*

---

### Post by MAFoElffen on 2016-06-22
I agree if there is a possibility of being at a large scale and for reuse.

But at a lower scale than needed for DEV-OPS, and if just an occasional-- you said you are looking for the 3rd occurrence of a specific string, but that you do not want to use a script(???).

But, because of the logic (3rd occurrence), you would use SED from a script right? SED is pattern matching, a Regular Expression. SED adds string manpuilulation. Great if you want to find something specific. But no logic within SED itself to keep track if that pattern match was the 3rd occurrence of that match... If just down and dirty, and the scale is small, I'll use SED (and called from scripts). If I need more detail, and I need to format the output found, then AWK. If in a program, then the same logic.

But if you are just looking for a string, do you really need that specific detail? SED and regular expressions are good if a match spans across a range of changes. What you are looking for is a specific string, and it is just data in string type. You can pattern match it as just a string. 

Immaterial of how you are doing pattern matching, in pattern matches, programmatically (technique), I like to store my pattern matches as a class constant or in a conf file, so that I can refer to them, re-use them, and find them when I need to ... less places to maintain them if that pattern changes.

Next, in your logic, is to set a counter to recognize the third occurrence, but to also set a flag when that happens, so that it just happens once for that, right? So if it occurs again for the same ... then what? Just thinking of the paths of that logic... But then I see that is it much simpler than that. (I overthought that.)

So a logical branch (if/then) on counter = 3, insert a new line...

By inserting a "newline", are you just formatting report output?

---

### Post by TheFu on 2016-06-22
The problem with trying to use just sed is that the config file has multiple sections and more than 1 section might match. Assuming the 3rd instance is the one to be modified is asking for code that will fail when the config file is changed upstream.  

Best to just use a template that YOU control, hence, why I suggested ansible.  I've written stuff like this in perl many, many times. It's a PITA and very fragile code. Any tiny issue with the config file breaks it.  Ansible makes this a 3 minute issue once the initial learning curve is done.

Ansible doesn't require that anything be installed on the remote system to work, agentless. That is another plus.  It doesn't require a "server" anywhere either.  Just a normal workstation.  Sure, sometimes, some remote systems might need 1 or 2 python modules to be installed - with 10.04, 12.04 and 14.04, I never had that need. Everything was already there with the default Ubuntu Server install. Haven't played with 16.04 enough to know, but there seems to be some python dependencies missing.

Of course, there could be issues not conveyed here that you are fighting which make Ansible a non-starter.

BTW, my 1st 5 minutes on a server ... [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

---

### Post by MAFoElffen on 2016-06-22
Yes. Upstream changes are... yes. I see the problem of that now. (I didn't think of that.) Then ansible does make a lot of sense.

And I like the idea of no additional agents loaded!!!

And with 16.04, it is the first version where there was core transitions to try to be just Python 3. I think a few months ago, there were just 2 minor changes left to make that happen.

---

