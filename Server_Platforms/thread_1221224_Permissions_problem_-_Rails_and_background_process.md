---
title: "Permissions problem - Rails and background processes"
date: 2009-07-23
forum: Server Platforms
---

### Post by wonderingwout on 2009-07-23
Hi,

I'm having a small permissions problem on my webserver.
A small situation sketch.

I'm running apache2 with Phusion Passenger and Rails 2.3.3.
To run background processes I'm using the whenever gem and the delayed_job plugin.

If I deploy the application as user 'stager', the delayed_job daemon won't start.
But with root it does.

Of course I don't want to run my application as root user.
So now I deploy as root and chown the whole site directory to stager:www-data afterwards.

But I'd rather have the stager do all that stuff.
So how can/should I configure the stager user to be able to start the daemons?

---

