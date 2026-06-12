---
title: "Guacamole RDP Not Working"
date: 2017-12-02
forum: Server Platforms
---

### Post by Kirk Schnable on 2017-12-02
Hello all,

I recently became interested in setting up Guacamole as a RDP front-end to some Windows systems of mine.  They are running Windows 7 so no funky RDP security from Server 2012 or anything like that going on.  It's just standard vanilla RDP and works fine with the simple "rdesktop" Linux client.

This is on a system running Ubuntu Server 16.04.3 from a fresh install intended as a purpose specific VM for Guacamole. 

I installed Guacamole from the repository and set up my connection:
```
root@server:~# dpkg --list | grep guac
ii  guacamole                           0.8.3-1.2                                    all          HTML5 web application for accessing remote desktops
ii  guacamole-tomcat                    0.8.3-1.2                                    all          Tomcat-based Guacamole install with VNC support
ii  guacd                               0.8.3-2                                      amd64        Guacamole proxy daemon
ii  libguac-client-rdp0:amd64           0.8.3-2                                      amd64        RDP support plugin for Guacamole
ii  libguac-client-vnc0:amd64           0.8.3-2                                      amd64        VNC support plugin for Guacamole
ii  libguac5:amd64                      0.8.3-2                                      amd64        Core Guacamole library used by guacd and client plugins
root@server:~# 
```

```
                <protocol>rdp</protocol>
                <param name="hostname">10.0.1.33</param>
                <param name="port">3389</param>
```

Unfortunately it's not working properly.  On the web UI, when I try to initiate a connection, it says "Connected, waiting for first update...", then "Connection closed".

In my syslog, I see a segfault occur:
```
Dec  2 17:45:43 server kernel: [153521.111995] guacd[21498]: segfault at 0 ip           (null) sp 00007f3f18801b98 error 14 in guacd[400000+5000]
```

I found a slightly dated bug report online from someone else having the same issue on Debian Jessie: [https://glyptodon.org/jira/si/jira.issueviews:issue-html/GUAC-1524/GUAC-1524.html](https://glyptodon.org/jira/si/jira.issueviews:issue-html/GUAC-1524/GUAC-1524.html)

I'm very surprised this seems to be broken out of the box, isn't anybody using this program and installing it from the repos?

Any suggestions on how I can troubleshoot this further?

Thanks!
Kirk

---

