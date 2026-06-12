---
title: "Ubuntu One does not start"
date: 2011-03-11
forum: Ubuntu One (CLOSED)
---

### Post by tayga17 on 2011-03-11
Hi All,
Im on Ubuntu 10.10 64bit. 
I having problem with syncing/starting Ubuntu One.
ubuntuone-lanch wont start and no files are sync. But I still able to sync my tomboy notes.

ubuntuone-launch command outputs:

```
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-launch", line 58, in <module>
    from ubuntu_sso.main import SSOCredentials
  File "/usr/lib/pymodules/python2.6/ubuntu_sso/main.py", line 42, in <module>
    from lazr.restfulclient.resource import ServiceRoot
  File "/usr/lib/python2.6/dist-packages/lazr/restfulclient/resource.py", line 34, in <module>
    import simplejson
  File "/usr/lib/pymodules/python2.6/simplejson/__init__.py", line 111, in <module>
    from decoder import JSONDecoder, JSONDecodeError
  File "/usr/lib/pymodules/python2.6/simplejson/decoder.py", line 29, in <module>
    NaN, PosInf, NegInf = _floatconstants()
  File "/usr/lib/pymodules/python2.6/simplejson/decoder.py", line 21, in _floatconstants
    _BYTES = '7FF80000000000007FF0000000000000'.decode('hex')
LookupError: unknown encoding: hex
```Thanks

---

### Post by nomko on 2011-03-11
To me it looks like something is wrong with the code. I don't think you can solve that.
 
I'm not using Ubuntu One actually, I'm using Dropbox which works very nice: [https://www.dropbox.com/](https://www.dropbox.com/).

---

### Post by tayga17 on 2011-03-11
I know about dropbox. But I need my Ubuntu fixed

---

### Post by duanedesign on 2011-03-14
> **tayga17 said:**
> Hi All,
Im on Ubuntu 10.10 64bit. 
I having problem with syncing/starting Ubuntu One.
ubuntuone-lanch wont start and no files are sync. But I still able to sync my tomboy notes.

ubuntuone-launch command outputs:

```
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-launch", line 58, in <module>
    from ubuntu_sso.main import SSOCredentials
  File "/usr/lib/pymodules/python2.6/ubuntu_sso/main.py", line 42, in <module>
    from lazr.restfulclient.resource import ServiceRoot
  File "/usr/lib/python2.6/dist-packages/lazr/restfulclient/resource.py", line 34, in <module>
    import simplejson
  File "/usr/lib/pymodules/python2.6/simplejson/__init__.py", line 111, in <module>
    from decoder import JSONDecoder, JSONDecodeError
  File "/usr/lib/pymodules/python2.6/simplejson/decoder.py", line 29, in <module>
    NaN, PosInf, NegInf = _floatconstants()
  File "/usr/lib/pymodules/python2.6/simplejson/decoder.py", line 21, in _floatconstants
    _BYTES = '7FF80000000000007FF0000000000000'.decode('hex')
LookupError: unknown encoding: hex
```Thanks

This looks like a problem with python.

What error do you get starting Ubuntu One with this command:

```
/usr/lib/ubuntuone-client/ubuntuone-syncdaemon
```

---

### Post by tayga17 on 2011-03-15
It is same error message

```
 /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
Traceback (most recent call last):
  File "/usr/lib/ubuntuone-client/ubuntuone-syncdaemon", line 38, in <module>
    from ubuntuone.syncdaemon.main import Main
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/main.py", line 30, in <module>
    from ubuntuone.syncdaemon import (
  File "/usr/lib/pymodules/python2.6/ubuntuone/syncdaemon/action_queue.py", line 29, in <module>
    import simplejson
  File "/usr/lib/pymodules/python2.6/simplejson/__init__.py", line 111, in <module>
    from decoder import JSONDecoder, JSONDecodeError
  File "/usr/lib/pymodules/python2.6/simplejson/decoder.py", line 29, in <module>
    NaN, PosInf, NegInf = _floatconstants()
  File "/usr/lib/pymodules/python2.6/simplejson/decoder.py", line 21, in _floatconstants
    _BYTES = '7FF80000000000007FF0000000000000'.decode('hex')
LookupError: unknown encoding: hex

```

---

