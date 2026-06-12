---
title: "PSAD Installed but unable to start service: Please help."
date: 2017-06-18
forum: Security
---

### Post by secondsurname on 2017-06-18
System: Ubuntu 16.04 LTS

As per the instructions detailed on the website bellow, I installed the PSAD IDS and configured it without incident.

[https://www.thefanclub.co.za/how-to/how-install-psad-intrusion-detection-ubuntu-1604-lts-server](https://www.thefanclub.co.za/how-to/how-install-psad-intrusion-detection-ubuntu-1604-lts-server)

However when I attempt to restart the service with the command "sudo psad -R", it returns the bellow error message:

[LIST]
[*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 10933. 
[/LIST]

Similarly, attempting to start the service with the command "sudo service psad start" returns the error:

[LIST]
[*]Job for psad.service failed because a configured resource limit was exceeded. See "systemctl status psad.service" and "journalctl -xe" for details. 
[/LIST]

The general usefulness of an IDS is always hindered by their difficulty to configure, or maybe thats just me, either way any help would be greatly appreciated :)
 - Thanks in Advance.

---

### Post by gordintoronto on 2017-06-21
The normal way to install PSAD would be through the software center. If you feel you need the very latest version, you should follow the official installation guide:
[http://cipherdyne.org/psad/docs/install.html](http://cipherdyne.org/psad/docs/install.html)

There is no chance whatsoever that I would install software based on instructions on a web site called "fanclub".

---

### Post by secondsurname on 2017-06-22
That is fair enough and thanks for the link. I tried installing and configuring it a few different ways in a Virtualbox VM, and it installed and operated perfectly on a clean Ubuntu 16.04 LTS install. There must have been something about my Ubuntu setup at the time which disagreed with it.

---

