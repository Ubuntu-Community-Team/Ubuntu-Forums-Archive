---
title: "Reconfiguring and restarting Apache from PHP securely"
date: 2009-01-31
forum: Security
---

### Post by shieldw0lf on 2009-01-31
I'm working on a project in which clients will be signing up to my service and making a payment, after which they should be able to see a subdomain that is assigned to them and begin adding content.

I'd like to be able to update my apache config files after an order is process and restart apache automatically, but all the information I've seen on how I might do that involves granting additional powers to the apache user, and I'm rather nervous about the security consequences of doing that.

So, I was thinking a better approach would be to store the details in the database and have a process that would check the database for changes on a regular basis, maybe once a minute.  

When it finds any changes, I'd like it to regenerate the apache config file and gracefully restart apache.

I'm running everything on a single server right now, but I'd like to have the ability to run multiple apache nodes and have a controller initiate this process on the nodes one at a time and not progress to the next until the current server comes back up, sending a message to me if it takes too long.

I've already moved my session storage to a postgresql/memcached configuration, so I figure I should be able to just restart these nodes and have a load balancer deal with the consequences.

My question is, what sort of tools would I need to make this work securely?  I'm not particularly experienced at administering Linux servers just yet, and I'm not sure what the right direction to go is.

I've been using command line PHP to do my unit testing at work, and am familiar with that, so my initial thought was to write one PHP script that would write the updated files to a known location on the network and run that using php-cli via cron every minute.  Then have another PHP script that would run on each node every minute, freshening the apache config and restarting apache if and when it's appropriate.

I'm a little concerned that I'm a man who understands a hammer and sees everything as a nail.  Is there a better approach to this problem?  It seems like something that would come up a lot in a web hosting environment...

---

### Post by Hobgoblin on 2009-01-31
Well from a Unix background I would create a file to flag when a restart was required and have a cron job run every x minutes and if the file exists then do whatever you need and restart apache.

---

