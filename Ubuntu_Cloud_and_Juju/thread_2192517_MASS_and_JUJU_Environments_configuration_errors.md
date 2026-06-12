---
title: "MASS and JUJU Environments configuration errors"
date: 2013-12-08
forum: Ubuntu Cloud and Juju
---

### Post by info-jitresourcesllc on 2013-12-08
I have been trying for days to get this to work, but I have not been able to identify the problem. I have configured the environments.yaml file to setup MAAS and Amazon AWS, but everytime I type the juju status command, I'm getting the erorrs listed below.   

error: Environments configuration error: /home/ideltoro/.juju/environments.yaml: while parsing a block mapping
  in "<string>", line 3, column 5:
        type: MAAS
        ^
expected <block end>, but found '<scalar>'
  in "<string>", line 6, column 20:
        admin-secret: 'nothing'
                       ^:
ideltoro@eburglxser01:~$ juju debug-log 
error: Environments configuration error: /home/ideltoro/.juju/environments.yaml: while scanning a simple key
  in "<string>", line 9, column 3:
      region defaults to us-east-1, ov ... 
      ^
could not found expected ':'
  in "<string>", line 10, column 3:
      region: us-east-1
      ^:

---

