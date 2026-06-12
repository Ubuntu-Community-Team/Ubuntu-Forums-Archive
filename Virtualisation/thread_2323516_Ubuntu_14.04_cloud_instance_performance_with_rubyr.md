---
title: "Ubuntu 14.04 cloud instance performance with ruby/rails apps and docker engine"
date: 2016-05-05
forum: Virtualisation
---

### Post by Mark_D. on 2016-05-05
We’ve noticed that Ubuntu 14.04 as a docker host as a cloud instance on ec2 doesn’t seem very performant when running our high transaction rails-based apps in docker containers.  Specifically when looking at app profiling (eg, new relic) we spend time in ruby doing… nothing.  All CPUs seem to have a good amount of 'overhead' spent in system time as well.  A half second here and there that rapidly adds up to slower overall response time for some of our apps.  Switching to CentOS (not our preferred choice; hence the post) as a docker host on a cloud instance seems to eliminate this wait time for these same rails apps.  Running the same app deployed in the same profile (eg, same instance sizes, same workers, etc.) natively on the Ubuntu 14.04 instance also does not present this degraded performance.

We've tried a variety of things, including:
* verifying we're not running into any limits anywhere on the system
* host networking
* cpu affinity bindings
* various sysctl tweaks
* compiling 'Real-Time group scheduling'

Does this ring a bell with anybody?  It's hauntingly familiar to this issue we found here: [http://stackoverflow.com/questions/35225037/docker-on-ubuntu-cant-saturate-cpu](http://stackoverflow.com/questions/35225037/docker-on-ubuntu-cant-saturate-cpu)

---

