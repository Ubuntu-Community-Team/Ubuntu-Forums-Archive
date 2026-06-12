---
title: "mod_perl installation problem"
date: 2011-05-15
forum: Server Platforms
---

### Post by tomkane1 on 2011-05-15
I have just created a new system with Ubuntu LTS 10.04. Everything there is working smoothly. I have apache2 loading and running automatically when I boot.

I want to add mod_perl(.so) to apache2. I have faithfully followed the mod_perl 2 installation directions in the documentation from perl.apache.org. All tests ran cleanly. 'make install' worked for both mod_perl and apache2 (the latter was required for creating mod_perl.so).

[Aside: I am aware that confusion exists in some nomenclature due to Debian/Ubuntu using different words for things, e.g., apache2.conf instead of httpd.conf. Note that the build did create a file named 'httpd.conf' file in one of my sub-directories.]

I see that the build of modules went into the directory:

    /home/tomkane/httpd

I sorta-kinda expected that the target directory would have been to something more along the lines of /usr/local/apache2 or some other more auspicious location than in my home directory. This is probably more of a naming problem. That is, I probably need to change a few name links somewhere.

When I check for running processes, I see that apache2 and its child processes are running. But when I try to stop apache2 with the following command:

    /home/tomkane/httpd/prefork/bin/apachectl stop

I get a return message from apachectl that httpd's not running and the usual stuff about resolving the server name.

It appears that apachectl wants to stop a process named 'httpd' whereas 'apache2' is what is running (as created at system installation time).

When I look into the /etc/init.d directory, I see that it contains apache2, not the new httpd that I just created when building mod_perl and the new apache2 httpd.

Now, perhaps I'm supposed to only rename the new 'httpd' executable to 'apache2' and copy it to the init.d directory. AND perhaps I'm supposed to only rename the newly created 'httpd.conf' file to 'apache2.conf' and copy it to the /etc/apache2 directory. OR do I need to copy everything from my build directory to another apache2 location?

Well, I feel a little gun shy about taking any drastic steps. Can anyone offer any suggestions or provide any clarification before I step off of a cliff?

Thanks for any advice.

---

