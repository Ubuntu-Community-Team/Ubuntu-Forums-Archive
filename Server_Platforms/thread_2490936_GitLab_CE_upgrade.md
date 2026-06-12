---
title: "GitLab CE upgrade"
date: 2023-09-21
forum: Server Platforms
---

### Post by civilpolisen on 2023-09-21
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292757&stc=1[/IMG]

We're using Gitlab CE and we do weekley updates. But during the summer break we didn't do any sudo updates...

There are so many instructions for all kinds of set-up's.... We're using Ubuntu, a quite common kind of sert-up!

[https://git.vertel.se/help/update/package/index.md#upgrade-using-a-manually-downloaded-package](https://git.vertel.se/help/update/package/index.md#upgrade-using-a-manually-downloaded-package)

Please guide me in the djungle of well documented success! Where is the installer line for me to use!?

---

### Post by civilpolisen on 2023-09-21
I've fount this page:
[https://gitlab-com.gitlab.io/support/toolbox/upgrade-path/?current=16.2.3&target=16.2.7&edition=ce](https://gitlab-com.gitlab.io/support/toolbox/upgrade-path/?current=16.2.3&target=16.2.7&edition=ce)

I enter the current version and the upgrade... and is given the upgrade line just to paste in the Terminal.
But all there is are errors like below!
Why is that!?


```
civilpolisen@edna:~$ sudo apt-get install gitlab-ce=16.2.7-ce.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '16.2.7-ce.0' for 'gitlab-ce' was not found
civilpolisen@edna:~$ 
```

Of-course, I've done much work before posting to this forum... but success is yet to come!
We use Ubuntu 20.04 and I would assume many others do as well...!

---

### Post by MAFoElffen on 2023-09-24
RE: [https://packages.gitlab.com/gitlab/gitlab-ce](https://packages.gitlab.com/gitlab/gitlab-ce), [https://docs.gitlab.com/ee/update/](https://docs.gitlab.com/ee/update/)

Looks like the repo's have downloadabe .deb packages, which you would download, then use dpkg to install. But, current is 16.4, not 16.2.7...

To do like you have posted, you would need their online repo added to your sources.list, And since you got that error, I would say that is not the method it was installed, right? As the Update/Upgrade Guide that I linked to above explains, you need to apply updates as the same method it was installed.

---

### Post by civilpolisen on 2023-10-03
Thank you very much! Based on your valuable input and my own skills... I managed to do the complete upgrade all to the latest version!
These notes are for myself and others that may find them useful!


```
civilpolisen@edna:~$ curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
[sudo] password for jakob: 
Detected operating system as Ubuntu/focal.
Checking for curl...
Detected curl...
Checking for gpg...
Detected gpg...
Running apt-get update... done.
Installing apt-transport-https... done.
Installing /etc/apt/sources.list.d/gitlab_gitlab-ce.list...done.
Importing packagecloud gpg key... done.
Running apt-get update... done.

The repository is setup! You can now install packages.

civilpolisen@edna:~$ sudo apt install gitlab-ce=16.2.7-ce.0

civilpolisen@edna:~$ sudo apt install gitlab-ce=16.3.0-ce.0

civilpolisen@edna:~$ sudo apt install gitlab-ce=16.4.0-ce.0

civilpolisen@edna:~$ sudo apt install gitlab-ce=16.4.1-ce.0


```

---

### Post by MAFoElffen on 2023-10-03
Glad it all worked out for you.

If resolved, please visit the "Thread Tools" link at the upper rihgt of the page to mark your thread as "Solved". That way other users can find what worked for you.

---

