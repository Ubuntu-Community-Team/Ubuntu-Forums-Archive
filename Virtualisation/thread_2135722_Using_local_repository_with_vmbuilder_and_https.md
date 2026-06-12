---
title: "Using local repository with vmbuilder and https"
date: 2013-04-15
forum: Virtualisation
---

### Post by onitlikesonic on 2013-04-15
[COLOR=#333333][FONT=Ubuntu Beta]I seem to be having problems using vmbuilder with a local https mirror "--mirror=https:///[COLOR=#222222][FONT=Ubuntu Mono]<my_internal_server>[/FONT][/COLOR]/ubuntu/" as shown below:[/FONT][/COLOR]

 ```
Process (['/usr/sbin/debootstrap', '--arch=amd64', 'precise', '/tmp/tmpYc0cOktmpfs', '<my_internal_server>/ubuntu/']) returned 1. stdout: I: Retrieving ReleaseE: Failed getting release file <my_internal_server>/ubuntu/dists/precise/Release
, stderr:
2012-10-18 10:36:36,429 INFO    : Unmounting tmpfs from /tmp/tmpYc0cOktmpfs
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 24, in <module>
    cli.main()
  File "/usr/lib/python2.7/dist-packages/VMBuilder/contrib/cli.py", line 216, in main
    distro.build_chroot()
  File "/usr/lib/python2.7/dist-packages/VMBuilder/distro.py", line 83, in build_chroot
    self.call_hooks('bootstrap')
  File "/usr/lib/python2.7/dist-packages/VMBuilder/distro.py", line 67, in call_hooks
    call_hooks(self, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/util.py", line 165, in call_hooks
    getattr(context, func, log_no_such_method)(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/plugins/ubuntu/distro.py", line 136, in bootstrap
    self.suite.debootstrap()
  File "/usr/lib/python2.7/dist-packages/VMBuilder/plugins/ubuntu/dapper.py", line 269, in debootstrap
    run_cmd(*cmd, **kwargs)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/util.py", line 120, in run_cmd
    raise VMBuilderException, "Process (%s) returned %d. stdout: %s, stderr: %s" % (args.__repr__(), status, mystdout.buf, mystderr.buf)
VMBuilder.exception.VMBuilderException: Process (['/usr/sbin/debootstrap', '--arch=amd64', 'precise', '/tmp/tmpYc0cOktmpfs', '<my_internal_server>/ubuntu/']) returned 1. stdout: I: Retrieving Release
E: Failed getting release file <my_internal_server>/ubuntu/dists/precise/Release
, stderr:
```
[COLOR=#333333][FONT=Ubuntu Beta]
I've checked that the files are in the correct place and i'm able to setup this using http instead of https. However this server will be providing https access only to the repos, the http is only temporarily open.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]
This might be due to the certificate not being valid on the https (since it's self signed) or due to the fact that vmbuilder doesn't support https? In either case how can i get this to work? (If it's the case of the invalid certificate I don't mind ignoring any checks)[/FONT][/COLOR]

---

