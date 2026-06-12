---
title: "Linaro Ubuntu 13.02 (for ARM) on Qemu: howto?"
date: 2013-03-25
forum: Virtualisation
---

### Post by sanderj on 2013-03-25
Hi,

Any help on getting Linaro Ubuntu for Arm running on Qemu?

[https://wiki.linaro.org/Platform/DevPlatform/Ubuntu/ImageInstallation](https://wiki.linaro.org/Platform/DevPlatform/Ubuntu/ImageInstallation) contains some instructions, which I interpreted into:


```
sander@appelboor:~$ sudo linaro-media-create --rootfs ext3 --image-file file.img --binary linaro-TARBALL.tar.gz --hwpack hwpack_linaro.tar.gz --dev vexpress

Traceback (most recent call last):
  File "/usr/bin/linaro-media-create", line 110, in <module>
    additional_option_checks(args)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/utils.py", line 342, in additional_option_checks
    "--hwpack argument (%s) is not a regular file" % hwpack)

linaro_image_tools.utils.InvalidHwpackFile: --hwpack argument (hwpack_linaro.tar.gz) is not a regular file

sander@appelboor:~$
```

So let's get a hwpack_linaro.tar.gz:

[http://www.linaro.org/downloads/](http://www.linaro.org/downloads/) contains a lot of downloads. This is what I tried:


sander@appelboor:~/linaro$ wget [https://releases.linaro.org/13.02/ubuntu/vexpress/hwpack_linaro-vexpress_20130224-256_armhf_supported.tar.gz](https://releases.linaro.org/13.02/ubuntu/vexpress/hwpack_linaro-vexpress_20130224-256_armhf_supported.tar.gz)




```
sander@appelboor:~/linaro$ sudo linaro-media-create --rootfs ext3 --image-file file.img --binary linaro-TARBALL.tar.gz --hwpack hwpack_linaro-vexpress_20130224-256_armhf_supported.tar.gz --dev vexpress
Traceback (most recent call last):
  File "/usr/bin/linaro-media-create", line 133, in <module>
    board_config.set_metadata(args.hwpacks, args.bootloader, args.dev)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/media_create/boards.py", line 499, in set_metadata
    'extra_boot_options')
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/media_create/boards.py", line 445, in get_metadata_field
    data, _ = cls.hardwarepack_handler.get_field(field_name)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/media_create/boards.py", line 185, in get_field
    new_data = parser.get_option(field)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/hwpack/config.py", line 500, in get_option
    return attrgetter(name)(self)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/hwpack/config.py", line 594, in extra_boot_options
    join_list_with=" ")
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/hwpack/config.py", line 443, in _get_bootloader_option
    raise ValueError("bootloader not set.")
ValueError: bootloader not set.
sander@appelboor:~/linaro$ 
```


So ... what should I download for "linaro-TARBALL.tar.gz"? Or is something else going on?

---

### Post by sanderj on 2013-03-25
[https://wiki.linaro.org/WorkingGroups/ToolChain/Outputs/QEMUVersatileExpress](https://wiki.linaro.org/WorkingGroups/ToolChain/Outputs/QEMUVersatileExpress) says

linaro-media-create --image_file vexpress.img --dev vexpress \
  --console ttyAMA0,38400n8 \
  --binary linaro-natty-nano-tar-20110228-0.tar.gz \
  --hwpack hwpack_linaro-vexpress_20110228-0_armel_supported.tar.gz

where to find those images for Linaro-Ubuntu 13.02?

---

### Post by sanderj on 2013-03-25
Update:

```
wget [https://releases.linaro.org/13.02/ubuntu/vexpress/hwpack_linaro-vexpress_20130224-256_armhf_supported.tar.gz](https://releases.linaro.org/13.02/ubuntu/vexpress/hwpack_linaro-vexpress_20130224-256_armhf_supported.tar.gz)
wget [https://releases.linaro.org/13.02/ubuntu/vexpress/linaro-quantal-developer-20130224-286.tar.gz](https://releases.linaro.org/13.02/ubuntu/vexpress/linaro-quantal-developer-20130224-286.tar.gz)

sander@appelboor:~/linaro$ ll
total 187484
drwxrwxr-x    2 sander sander      4096 mrt 25 23:13 ./
drwx--x---+ 173 sander sander     32768 mrt 25 22:53 ../
-rw-rw-r--    1 sander sander  42233857 feb 24 08:35 hwpack_linaro-vexpress_20130224-256_armhf_supported.tar.gz
-rw-rw-r--    1 sander sander 149700180 feb 24 08:21 linaro-quantal-developer-20130224-286.tar.gz
sander@appelboor:~/linaro$ 

sander@appelboor:~/linaro$ linaro-media-create --image_file vexpress.img --dev vexpress --console ttyAMA0,38400n8 --binary linaro-quantal-developer-20130224-286.tar.gz --hwpack hwpack_linaro-vexpress_20130224-256_armhf_supported.tar.gz 
Traceback (most recent call last):
  File "/usr/bin/linaro-media-create", line 133, in <module>
    board_config.set_metadata(args.hwpacks, args.bootloader, args.dev)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/media_create/boards.py", line 499, in set_metadata
    'extra_boot_options')
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/media_create/boards.py", line 445, in get_metadata_field
    data, _ = cls.hardwarepack_handler.get_field(field_name)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/media_create/boards.py", line 185, in get_field
    new_data = parser.get_option(field)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/hwpack/config.py", line 500, in get_option
    return attrgetter(name)(self)
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/hwpack/config.py", line 594, in extra_boot_options
    join_list_with=" ")
  File "/usr/lib/python2.7/dist-packages/linaro_image_tools/hwpack/config.py", line 443, in _get_bootloader_option
    raise ValueError("bootloader not set.")
ValueError: bootloader not set.
sander@appelboor:~/linaro$


sander@appelboor:~/linaro$ linaro-media-create --version
linaro-media-create 2012.09-1 : usage: qemu-arm [options] program
[arguments...]
sander@appelboor:~/linaro$
```

[https://bugs.launchpad.net/linaro-image-tools/+bug/1056977](https://bugs.launchpad.net/linaro-image-tools/+bug/1056977) says:

> When invoking linaro-media-create with a hwpack that has multiple bootloader sections and without the --bootloader command line argument you get:

So now I need a bootloader?

Tips welcome.

---

