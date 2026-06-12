---
title: "Ubuntu Cloud Infrastructure Juju Boostrap error"
date: 2012-01-30
forum: Ubuntu Cloud and Juju
---

### Post by nodetx on 2012-01-30
Hi, while following this document:
[https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure)
 
I get to step 2 where I need to configure a yaml file
 
I vim it and here's my config:
 
```
juju: environments
environments:
  orchestra:
    type: orchestra
    # Specify the orchestra server's IP address
    orchestra-server: 192.168.2.41
    # Specify storage. In this case we are using webdav installed by orchestra.
    storage-url: [http://192.168.2.41/webdav](http://192.168.2.41/webdav)
    # Specify cobbler's usr/pass
    orchestra-user: cobbler
    orchestra-pass: mypasswordforcobbleidefinedinsetup
    admin-secret: arandomthingijusttypedinnow
    # Branch from where we will install ensemble
    # juju-branch: lp:juju
    # Mangement classes
    acquired-mgmt-class: orchestra-juju-acquired
    available-mgmt-class: orchestra-juju-available
```
 
then I get this message when I run juju bootstrap
 
```
error: Environments configuration error: /home/node/.juju/environments.yaml: environments.orchestra.default-series: required value not found

```
 
I checked and found this other doc on configuring juju with orchestra for local storage:
[https://help.ubuntu.com/community/Orchestra/Juju](https://help.ubuntu.com/community/Orchestra/Juju)
 
I don't think I'm following the BZR branch so I should just need to run ```
juju boostrap
``` I think
 
While looking at the above link, I found it also has a sample config file. There is one slight difference between the config samples - on the last link there the sample has the IP address for the configuration as
 
```
  # Specify the orchestra server's IP address
    orchestra-server: '192.168.2.41'
    # Specify storage. In this case we are using webdav installed by orchestra.
    storage-url: '[http://192.168.2.41/webdav'](http://192.168.2.41/webdav')

```
 
while the original document I was followed doesn't have the ' marks between the IP addresses. I tried it both ways, I tried it with using localhost and 'localhost' and I tried reboots between every config change just for extra grins.
 
```
  # Specify the orchestra server's IP address
    orchestra-server: 192.168.2.41
    # Specify storage. In this case we are using webdav installed by orchestra.
    storage-url: [http://192.168.2.41/webdav](http://192.168.2.41/webdav)

```
 
I don't know what the problem here is, and the only thing I could find online that even remotely appeared to be someone else with this problem was a linked to this:
[http://pastebin.com/NNqBkiNn](http://pastebin.com/NNqBkiNn)
 
That link goes to someone who posted the same error message that I get (no solution is on that web link) - basically, if I read this right, there's a configuration error with my environments.yaml and based on the available documentation, I just don't see where I'm going wrong...

---

### Post by dowdberry on 2012-02-02
My .juju/environments.yaml includes two other fields (and likely the default-series is the one you need):
    juju-origin: ppa
    default-series: oneiric

---

### Post by nodetx on 2012-02-03
Thanks for the response! I'll try it out and report back on this thread

---

### Post by nodetx on 2012-02-03
Yup, simply adding 
 
[HTML]default-series: oneiric[/HTML]
 
as the last line of my yaml config file did the trick! Thanks for the help. Now I am getting another error regarding "Cloud not find any Cobbler systems marked as available and confired for network boot." but I haven't even started researching that one yet and I'll post a fresh thread if I need help there.
 
Once again, thanks for getting me over the hump on this error!

---

### Post by wintrmute2 on 2012-03-13
> **nodetx said:**
> 
Now I am getting another error regarding "Cloud not find any Cobbler systems marked as available and confired for network boot." but I haven't even started researching that one yet and I'll post a fresh thread if I need help there.


Hi,
I couldn't find any other threads by you on this topic, so I wondered if you had solved the "No cobbler systems available" issue? If so, what did you do?

Cheers,
Toby

---

### Post by claytronic on 2012-03-15
I am having the same problem. Any luck on finding a solution?

:Edit:

Pretty simple answer at:
[http://askubuntu.com/questions/100107/cant-succesfully-run-juju-bootstrap](http://askubuntu.com/questions/100107/cant-succesfully-run-juju-bootstrap)

---

### Post by wintrmute on 2012-03-15
Thanks! That looks like what it'll be.
That was so NOT clear from any documentation I had read :(

---

