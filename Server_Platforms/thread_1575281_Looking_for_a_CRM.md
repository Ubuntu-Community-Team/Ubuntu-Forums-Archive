---
title: "Looking for a CRM"
date: 2010-09-15
forum: Server Platforms
---

### Post by uge on 2010-09-15
Hi all !

I'm looking for a good CRM application.

My environment is as follow :

[LIST]
[*]Serveur : Ubuntu 8.04 LTS Server x64
[*]Desktops running on Mac OS X / Windows XP / Windows 7
[/LIST]

So I'm looking, ideally, for an application that would be installed on my server, and accessible through a web interface so it'd be cross-platform for the "clients".

I'd also like the software to be able to deal with permissions.

So the admin would have access to everything, but a representative would only have access to the contacts that were linked to him.

Then if a representative leaves, the admin can reassign contacts to another representative and this new rep. have access to these contacts.

What I'm expecting from such a CRM is for our representative to be able to input contact infos, and make follow-ups. Also set attributes for every contact.
The application should handle the follow-up and notify the representative associated with a contact that it is time for him/her to call that contact, etc.

The representative should be able to input what he's done everything (ex : called - no answer - left message on mailbox, etc.) and set the next reminder.
He should also document everytime he meets one of the contact, and/or if it let to a sale, etc.

It'd be great also if there could be different levels of permission.
Admin has all priviledges.
Team leader has access to all the contacts of the reprensentatives in his team.
And representatives have only access to the contacts that were assigned to them.

Finally, security features would be great (but not a critical factor)... for example, given that "clients" access the system through a web interface : SSL cerficates, etc.


In conclusion, I have never experienced a CRM before so any suggestion are much welcomed.


THANK YOU !

---

### Post by KegHead on 2010-09-15
Hi!

I'm looking at Sugar.

KegHead

---

### Post by DaithiF on 2010-09-15
+1 SugarCRM

---

### Post by uge on 2010-09-15
Hi guys !

Thanks for the quick reply !

I'd like to know at which point SugarCRM is "open source"
I'm worried that the Open Source version is just a limited version of SugarCRM, designed to make you want to buy the "Pro" package.

Also, there is no live demo, and I'd like to know if it can handle permissions like I described ?


Thanks !!

---

### Post by DaithiF on 2010-09-16
Sugarcrm follows an 'open-core' model, where yes, the basic version is free to use but certain features are available only in the pro. version which you have to pay for.  How far you get with the free version will depend on your particular requirements.  There do offer a 'live demo' free trial (where they host an instance for you), or you can just download and install the community edition to try it.

As far as i remember the main differences pro. vs community, at least as they impacted on my requirements were (1) a reporting module and (2) a teams module.

The other open-source CRM to consider is vTiger, but I haven't used it so can't comment.

---

### Post by uge on 2010-09-16
> **DaithiF said:**
> As far as i remember the main differences pro. vs community, at least as they impacted on my requirements were (1) a reporting module and (2) **a teams module.**

Hi !

Now you've caught my interest !

What does the teams module do ?

Or, if you prefer, what does not having the teams module prevent you to do ?


Thank you !!

---

### Post by DaithiF on 2010-09-17
> **uge said:**
> Hi !

Now you've caught my interest !

What does the teams module do ?

Or, if you prefer, what does not having the teams module prevent you to do ?


Thank you !!

This is from memory, we quickly upgraded to professional edition, so its possible I may not be 100% right here, but here goes:

Without teams, the way permissions work is as follows:
You can be an admin, with access to everything, or
You can be a user who has access to everthing, or
You can be a user who has access only to your own items (items created by you)

With Teams (& the related idea of Roles that comes with it), you add extra levels of granularity.  So for example, you could set up separate teams for Sales and Finance, and then limit individuals access to one or other (or both) of those teams.  For more info see: [http://www.sugarcrm.com/crm/products/capabilities/sales/teams.html](http://www.sugarcrm.com/crm/products/capabilities/sales/teams.html)

---

### Post by uge on 2010-09-17
> **DaithiF said:**
> This is from memory, we quickly upgraded to professional edition, so its possible I may not be 100% right here, but here goes:

Without teams, the way permissions work is as follows:
You can be an admin, with access to everything, or
You can be a user who has access to everthing, or
You can be a user who has access only to your own items (items created by you)

Hi again !

I know it's been a while and you didn't experience the free Open-Source version long but:
Given I can set a user to have access only to his own items
And given that user (employee) leaves our company, can I re-assign his items to another user, who will in term have access to his own items and the one he's been assigned ?

Because if that's so, then the Open-Source version of SugarCRM will be perfect for me.

If not, then I'll go with vTiger...

BTW, for anyone interested, [here's a nice article]("http://www.forecastingclouds.com/articles/33058/the-top-10-open-source-crm-applications/") with a great chart at the bottom.
It's quite complete, and very recent ! (posted less than a month ago!)


THANKS !! \\:D/

---

### Post by DaithiF on 2010-09-17
> **uge said:**
> Hi again !

I know it's been a while and you didn't experience the free Open-Source version long but:
Given I can set a user to have access only to his own items
And given that user (employee) leaves our company, can I re-assign his items to another user, who will in term have access to his own items and the one he's been assigned ?

Because if that's so, then the Open-Source version of SugarCRM will be perfect for me.

If not, then I'll go with vTiger...

BTW, for anyone interested, [here's a nice article]("http://www.forecastingclouds.com/articles/33058/the-top-10-open-source-crm-applications/") with a great chart at the bottom.
It's quite complete, and very recent ! (posted less than a month ago!)


THANKS !! \\:D/

Yep, sugar does that, you can assign records en-mass quite easily.

---

### Post by Pierrot Lafouine on 2010-10-13
Hi
How do we install SugarCRM ?
Trying to follow this :
[http://www.sugarforge.org/content/installation/index.php#1095325](http://www.sugarforge.org/content/installation/index.php#1095325)

But stopped at line : /var/www/html/ (Linux/Apache)
There are no folder html.
I have Ubuntu version 8.04 LTS

Thanks

---

### Post by SeijiSensei on 2010-10-14
Looks like it's expecting a RedHat or CentOS server where /var/www/html is the default website location.  Either create the directory yourselves manually, or tell the installer to use /var/www, the default Ubuntu location, instead.

If you start installing other "enterprise" software for Linux, you're going to find the scenario repeated.  Most corporate Linux usage relies on RHEL or derivatives.  Ubuntu might be a great desktop OS, but it's definitely an also-ran in the server room.

---

### Post by Pierrot Lafouine on 2010-10-14
Hi
Thank for the answer.
I created and copy files into folder, I'm able to run wizzard from
web browser, but now is asking a username and a pwd. I tried all I
could, without success.  This is the error msg:

The provided database host, username, and/or password is invalid,
and a connection to the database could not be established. Please
enter a valid host, username and password. 2005: Unknown MySQL
server host 'localhost' (1)).

Any idea wich username and pwd I have to use ?

Thanks,

---

