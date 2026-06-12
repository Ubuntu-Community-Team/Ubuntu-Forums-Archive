---
title: "OpenStack Juno Swift installation problem."
date: 2015-02-16
forum: Ubuntu Cloud and Juju
---

### Post by David_Barman on 2015-02-16
I am following the OpenStack install guide for 14.04.  I am up to the point of "swift" to create the account rings.
I created the account.builder file with the command:  "swift-ring-builder account.builder create 10 3 1".
That worked fine.
When I go to the next step:  "swift-ring-builder account.builder add r1z1-10.0.0.51:6002/sda1 100". I get the following error and not sure what to do:

[COLOR=#0000ff]*root@OSCN:/etc/swift# swift-ring-builder account.builder add rlz1-10.0.0.51:6002/sdb1 100*[/COLOR]
[COLOR=#0000ff]*Traceback (most recent call last):*[/COLOR]
[COLOR=#0000ff]*  File "/usr/bin/swift-ring-builder", line 24, in <module>*[/COLOR]
[COLOR=#0000ff]*    sys.exit(main())*[/COLOR]
[COLOR=#0000ff]*  File "/usr/lib/python2.7/dist-packages/swift/cli/ringbuilder.py", line 866, in main*[/COLOR]
[COLOR=#0000ff]*    Commands.__dict__.get(command, Commands.unknown.im_func)()*[/COLOR]
[COLOR=#0000ff]*  File "/usr/lib/python2.7/dist-packages/swift/cli/ringbuilder.py", line 377, in add*[/COLOR]
[COLOR=#0000ff]*    for new_dev in _parse_add_values(argv[3:]):*[/COLOR]
[COLOR=#0000ff]*  File "/usr/lib/python2.7/dist-packages/swift/cli/ringbuilder.py", line 92, in _parse_add_values*[/COLOR]
[COLOR=#0000ff]*    region = int(devstr[1:i])*[/COLOR]
[COLOR=#0000ff]*ValueError: invalid literal for int() with base 10: ''*[/COLOR]


Any ideas would be greatly appreciated!

---

### Post by sakman2 on 2015-03-04
I had the exact same error - but my fix was that I mistakenly used "ells" instead of "ones" in r1z1.

---

