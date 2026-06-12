---
title: "Can't uninstall Cloudfoundry from ubuntu server!"
date: 2012-03-10
forum: Server Platforms
---

### Post by bayonetblaha on 2012-03-10
I suspected Cloudfoundry as the troublemaker for a rails issue I was having. Now I'm just alarmed that I can't get it out of my package system! I've tried every command I could find on google. I generally get the same errors (involving STARTING cloudfoundry, among other nonsense!), and then a dpkg error.

nelson@nelnet:~$ sudo apt-get purge cloudfoundry-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cloudfoundry-server*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 60.3 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 175555 files and directories currently installed.)
Removing cloudfoundry-server ...
 * Stopping Cloud Foundry Server
/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require': no such file to load -- eventmachine (LoadError)
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
        from bin/vcap:25:in `<main>'
invoke-rc.d: initscript cloudfoundry-server, action "stop" failed.
dpkg: error processing cloudfoundry-server (--purge):
 subprocess installed pre-removal script returned error exit status 1
 * Starting Cloud Foundry Server
/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require': no such file to load -- eventmachine (LoadError)
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
        from bin/vcap:25:in `<main>'
invoke-rc.d: initscript cloudfoundry-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cloudfoundry-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by soulreaver1 on 2012-03-11
First of all, manually disable the cloudfoundry-server service, next try to purge it, same as you have tried before. If the problem would still appear, try to force it: 
```
sudo apt-get -f purge cloudfoundry-server
```

---

