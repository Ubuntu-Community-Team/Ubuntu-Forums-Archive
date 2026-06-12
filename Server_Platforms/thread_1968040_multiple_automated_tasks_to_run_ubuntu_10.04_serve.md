---
title: "multiple automated tasks to run ubuntu 10.04 server"
date: 2012-04-28
forum: Server Platforms
---

### Post by lrpr on 2012-04-28
I need to run automated tasks every 15. The tasks is for my  server (call it server A, Ubuntu 10.04 LAMP) to query for updates to  another server (Server B).
  I have multiple users to query for, possibly 14 (or more) users. As  of now, the scripts are written in PHP. They do the following: 
  
[LIST=1]
[*]request Server B for updates on users
[*]If Server B says there are updates, then Server A retrieves the updates
[*]In Server A, update DB with the new data for the users in
[*]run calculations in server A
[*]send prompts to users that I received data updates from.
[/LIST]
  I know **cron jobs** might be the way to go, but there  could be a scenario where I might have a cron job for every user. Is  that reasonable? Or should I force it to be one cron job querying data  for all my users?
  Also, the server I'm querying has a java api that I can use to query  it. Which means I could develop a java servlet to do the same. I've had  trouble with this approach but I'm looking for feedback if this is the  way to go. I'm not familiar with Tomcat and I don't fully understand it  yet.
  Summary: I need my server to run tasks automatically every 15 mins,  the requests data from another server, updates its DB and then send  prompts to users. What's are recommended approaches? 
  Thanks for your help!

---

### Post by josephmills on 2012-04-28
puppet chef salt all sound like they fit the bill  

puppet 
[http://projects.puppetlabs.com/projects/1/wiki/Puppet_Ubuntu](http://projects.puppetlabs.com/projects/1/wiki/Puppet_Ubuntu)
[http://www.youtube.com/watch?v=US8ZpjgEhUg](http://www.youtube.com/watch?v=US8ZpjgEhUg)

chef 
[http://www.opscode.com/chef/](http://www.opscode.com/chef/)

salt 
[http://saltstack.org/](http://saltstack.org/)

---

### Post by lrpr on 2012-04-29
Thanks for all those suggestions. I wasn't familiar with any of them. I'll definitely take a look at them.

---

### Post by Jonathan L on 2012-04-29
> Summary: I need my server to run tasks automatically every 15 mins,  the requests data from another server, updates its DB and then send  prompts to users. What's are recommended approaches? 
  Thanks for your help!

For maintaining synchronised user database, the various links are good ideas.  Also, of course, NIS and LDAP.

For doing the calculations (not clear what they might be) ... cronjobs sound perfectly great.  I'd head for one big job for them all.

Hope that's helpful.

Kind regards,
Jonathan.

---

