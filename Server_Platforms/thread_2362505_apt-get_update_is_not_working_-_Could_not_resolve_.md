---
title: "apt-get update is not working - Could not resolve 'cusxwtc-mwg4'"
date: 2017-05-29
forum: Server Platforms
---

### Post by fasoulas on 2017-05-29
I have an issue where the apt-get update command is not working correctly.

Eg below is an output of the command:
```

administrator@appserver:/var/lib/apt$ sudo apt-get update
Err:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Could not resolve 'cusxwtc-mwg6'
Err:3 http://pkg.jenkins.io/debian-stable binary/ InRelease
  Could not resolve 'cusxwtc-mwg4'
Err:4 http://cy.archive.ubuntu.com/ubuntu xenial InRelease
  Could not resolve 'cusxwtc-mwg4'
Err:2 http://ppa.launchpad.net/openjdk-r/ppa/ubuntu xenial InRelease
  Could not resolve 'cusxwtc-mwg6'
Err:5 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease
  Could not resolve 'cusxwtc-mwg6'
Err:6 http://cy.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Could not resolve 'cusxwtc-mwg4'
Err:7 http://cy.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Could not resolve 'cusxwtc-mwg4'
Hit:8 https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu xenial InRelease
Hit:9 https://packages.gitlab.com/runner/gitlab-ci-multi-runner/ubuntu xenial InRelease
Reading package lists... Done
W: Failed to fetch http://cy.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Could not resolve 'cusxwtc-mwg4'
W: Failed to fetch http://cy.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Could not resolve 'cusxwtc-mwg4'
W: Failed to fetch http://cy.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Could not resolve 'cusxwtc-mwg4'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Could not resolve 'cusxwtc-mwg6'
W: Failed to fetch http://pkg.jenkins.io/debian-stable/binary/InRelease  Could not resolve 'cusxwtc-mwg4'
W: Failed to fetch http://ppa.launchpad.net/openjdk-r/ppa/ubuntu/dists/xenial/InRelease  Could not resolve 'cusxwtc-mwg6'
W: Failed to fetch http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/xenial/InRelease  Could not resolve 'cusxwtc-mwg6'
W: Some index files failed to download. They have been ignored, or old ones used instead.
administrator@appserver:/var/lib/apt$


```

I have tried the command host -v cy.archive.ubuntu.com and it verifies the domain name is resolved.

I have also noticed that in each failed repository retrieval i can see the  Could not resolve 'cusxwtc-mwg4' which doesn't make any sense. I have tried searching for it but i get no results.

The same message is shown (Could not resolve 'cusxwtc-mwg4') if i also try to install anything using apt-get.

What does the cusxwtc-mwg4 mean and how can this issue be resolved?

---

