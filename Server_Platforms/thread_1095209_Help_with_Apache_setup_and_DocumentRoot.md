---
title: "Help with Apache setup and DocumentRoot"
date: 2009-03-13
forum: Server Platforms
---

### Post by radopod on 2009-03-13
Hi All.

Hoping that someone may be able to help us out here.

Situation is this. We have a setup where our web root is in /var/www. We use Joomla for our main site. We hate having to put all our other apps/subfolders/etc in the Joomla directory as it gets very cluttered. So we would like to have Joomla in it's own directory. So instead of having /var/www/joomla/phpbb for example, we want to have /var/www/joomla and /var/www/phpbb. Now the problem comes in with getting apache to play nice with this setup. We basically want our main domain (mydomain.com) to point to the /joomla directory but if a user browses to mydomain.com/phpbb, they are in the /phpbb directory. Makes sense? Is this possible? I have tried a couple different methods, one being to subdomain everything with their own virtual hosts (which is not optimal). The other is using a couple different rewrites which does the trick at first, but then all subsequent links in Joomla are mydomain.com/joomla instead of just mydomain.com.

Any ideas?

---

