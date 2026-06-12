---
title: "Upgrading from Ubuntu 14.04 to 16.04, Tomcat 7  propose NoSuchMethodError (s)"
date: 2017-02-23
forum: Server Platforms
---

### Post by herr.drake on 2017-02-23
The issue is well known, but no solution is available at the moment.
Apparently, is with the Tomcat 7 module available in the Ubuntu Repo
and automatically installed during the upgrades of the operative system.

Having an instance of Tomcat 7 working and configured with Alfresco+Share,
once an OS upgrade from Ubuntu 14.04 to 16.04 is performed,
the applications installed in the webapps folder throw many SEVERE ERRORS:

```
SEVERE: StandardWrapper.Throwable
java.lang.NoSuchMethodError: java.util.concurrent.ConcurrentHashMap.keySet()
```

Specifically the issue affects the following configuration:
[LIST]
[*]Ubuntu 16.04
[*]Tomcat 7
[*]Alfresco 4.2.c
[/LIST]
The bug is documented and analyzed in many forum:
[LIST]
[*][https://bz.apache.org/bugzilla/show_bug.cgi?id=55554](https://bz.apache.org/bugzilla/show_bug.cgi?id=55554)
[*][https://groups.google.com/forum/#!topic/xnat_discussion/DOy5qUKY0zY](https://groups.google.com/forum/#!topic/xnat_discussion/DOy5qUKY0zY)
[*]etc.
[/LIST]
This breaks working installations without any Tomcat major version updates.

In my opinion this is a bug, but no solution for a distributed package is apparently available at the moment.

Solutions proposed in other forums, require building Tomcat from other sources, or upgrading the version.
This create additional effort for the sysadmin, with the risk that other issues appear within the originally working installation (version compatibilities, etc.)

Thank you for proposing a solution.

---

### Post by DuckHook on 2017-02-23
Welcome to the forums, herr.drake.

Please refrain from using non-standard fonts and formatting when posting as this is difficult to read. Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

I have also moved your post to a forum that is more relevant to your issue.

---

