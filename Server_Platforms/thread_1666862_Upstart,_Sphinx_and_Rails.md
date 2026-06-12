---
title: "Upstart, Sphinx and Rails"
date: 2011-01-14
forum: Server Platforms
---

### Post by g0nzo on 2011-01-14
Hey,

I've got Ruby on Rails application running on Ubuntu 10.04. My app requires Sphinx server to run and currently it's not started automatically after server reboot. I wanted to use upstart to handle it, but I can't make it work at all.

Here's the upstart script I got:

```
description "Sphinx"

start on startup
stop on shutdown

exec /bin/su - deploy -c "cd /var/www/apps/my_app/current && RAILS_ENV=production bundle exec rake thinking_sphinx:start"

```

It calls rake task which in turn starts searchd with proper config file.

After running "sudo start my_service" it just hangs. If I change path in the command above to some fake one, it still hangs - no difference. If I press CTRL+C while it hangs and try to start it again, it says that my_service is already running, but searchd daemon is actually not running. I tried adding "expect fork", but it doesn't change anything.

If I manually run the command upstart is supposed to run with sudo - it works.

Any ideas?

[EDIT] I got it working with init.d script using exactly the same command, but upstart looks so much nicer :)

---

### Post by rubylaser on 2011-01-14
And that's why I still use init.d for all my homemade init scripts.  I'll try to transition them to upstart at some point though.  I haven't done any Rails development in a while other than maintaining old applications.  I'm going to have to tryout Thinking Sphinx.

---

