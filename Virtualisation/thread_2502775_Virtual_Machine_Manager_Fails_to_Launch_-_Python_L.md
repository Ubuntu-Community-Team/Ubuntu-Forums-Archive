---
title: "Virtual Machine Manager Fails to Launch - Python Lib Error"
date: 2024-11-28
forum: Virtualisation
---

### Post by duggers on 2024-11-28
Hi all,

This issue is well out of my knowledge area. I've tried reinstalling virt-manager but the error persists and I'm out of ideas.

Below is the error I see when running it from the terminal. Please could someone point me in the right direction?

Traceback (most recent call last):
  File "/usr/bin/virt-manager", line 6, in <module>
    from virtManager import virtmanager
  File "/usr/share/virt-manager/virtManager/virtmanager.py", line 19, in <module>
    from virtinst import BuildConfig
  File "/usr/share/virt-manager/virtinst/__init__.py", line 50, in <module>
    from virtinst.domain import *  # pylint: disable=wildcard-import
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/share/virt-manager/virtinst/domain/__init__.py", line 5, in <module>
    from .blkiotune import DomainBlkiotune
  File "/usr/share/virt-manager/virtinst/domain/blkiotune.py", line 8, in <module>
    from ..xmlbuilder import XMLBuilder, XMLChildProperty, XMLProperty
  File "/usr/share/virt-manager/virtinst/xmlbuilder.py", line 16, in <module>
    from .xmlapi import XMLAPI
  File "/usr/share/virt-manager/virtinst/xmlapi.py", line 7, in <module>
    import libxml2
  File "/usr/lib/python3/dist-packages/libxml2.py", line 1, in <module>
    import libxml2mod
ImportError: /usr/lib/vmware/libxml2.so.2: version `LIBXML2_2.9.11' not found (required by /usr/lib/python3/dist-packages/libxml2mod.cpython-312-x86_64-linux-gnu.so)

Thanks
Ian

---

