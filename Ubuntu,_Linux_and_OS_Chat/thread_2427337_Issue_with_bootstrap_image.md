---
title: "Issue with bootstrap image"
date: 2019-09-20
forum: Ubuntu, Linux and OS Chat
---

### Post by cloudsigma on 2019-09-20
[COLOR=#1D1C1D][FONT=Slack-Lato]Dear community,[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]We operate a cloud infrastructure where we maintain a library with various preinstalled images with Linux/Unix. We are currently working to provide an Ubuntu installation with JUJU.[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]In the process, we are getting an error which halts the progress.[/FONT][/COLOR]
[COLOR=#1D1C1D][FONT=Slack-Lato]After issuing the command:[/FONT][/COLOR][HTML]juju bootstrap cloudsigma --debug[/HTML][COLOR=#1D1C1D][FONT=Slack-Lato]we get this output:[/FONT][/COLOR][HTML]17:02:08 ERROR juju.cmd.juju.commands bootstrap.go:697 failed to bootstrap model: cannot start bootstrap instance: failed start instance: Failed to query drive template: 401 None
17:02:08 DEBUG juju.cmd.juju.commands bootstrap.go:698 (error details: [{/build/juju/parts/juju/go/src/github.com/juju/juju/cmd/juju/commands/bootstrap.go:772: failed to bootstrap model} {/build/juju/parts/juju/go/src/github.com/juju/juju/environs/bootstrap/bootstrap.go:562: } {/build/juju/parts/juju/go/src/github.com/juju/juju/environs/bootstrap/bootstrap.go:471: } {/build/juju/parts/juju/go/src/github.com/juju/juju/provider/common/bootstrap.go:56: } {/build/juju/parts/juju/go/src/github.com/juju/juju/provider/common/bootstrap.go:212: cannot start bootstrap instance} {/build/juju/parts/juju/go/src/github.com/juju/juju/provider/cloudsigma/environinstance.go:81: failed start instance: Failed to query drive template: 401 None}])
17:02:08 DEBUG juju.cmd.juju.commands bootstrap.go:1332 cleaning up after failed bootstrap
17:02:08 INFO  juju.provider.common destroy.go:21 destroying model "controller"
17:02:08 INFO  juju.provider.common destroy.go:32 destroying instances
17:02:08 ERROR juju.cmd.juju.commands bootstrap.go:1334 error cleaning up: destroying instances: 400 Bad Request
17:02:09 INFO  cmd supercommand.go:502 command finished[/HTML]

[COLOR=#1D1C1D][FONT=Slack-Lato]Can we get some advice as to what is causing this behavior, and perhaps what we can do differently? Thanks in advance![/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2019-09-20
Could you also include this:
```
which juju
```
Did you miss this? "Failed to query drive template: 401 None"

---

### Post by cloudsigma on 2019-10-02
Hello @1fallen,

Thank you for your answer! 

The output of ```
which juju
``` is 

```
root@Mk:/home/cloudsigma# which juju/snap/bin/juju
root@Mk:/home/cloudsigma# 

```

Yes, we noticed the error  [COLOR=#000000]"Failed to query drive template: 401 None", but we have a drive in the library with Juju installed on it. I am not sure how we should resolve that error. Could you please advise us? 

Thank you in advance! [/COLOR]

---

