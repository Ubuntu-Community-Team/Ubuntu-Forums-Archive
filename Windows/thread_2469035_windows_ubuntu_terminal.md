---
title: "windows ubuntu terminal"
date: 2021-11-17
forum: Windows
---

### Post by jimninja on 2021-11-17
hi, 

I have a pc with linux ubuntu but also a laptop with windows and I installed the windows ubuntu terminal to try and I use open wrt firmware for my routers and I make my own build. So, now I compiled a build on my windows via the ubuntu terminal and everything is working but I can't find where is the folder?? Idea? Open wrt folder....

thanks

---

### Post by CharlesA on 2021-11-17
It's located in a virtual file system. You should be able to access it via this network path from windows:
```
\\wsl$
```

[https://www.howtogeek.com/426749/how-to-access-your-linux-wsl-files-in-windows-10/](https://www.howtogeek.com/426749/how-to-access-your-linux-wsl-files-in-windows-10/)

---

### Post by jimninja on 2021-11-18
> **CharlesA said:**
> It's located in a virtual file system. You should be able to access it via this network path from windows:
```
\\wsl$
```

[https://www.howtogeek.com/426749/how-to-access-your-linux-wsl-files-in-windows-10/](https://www.howtogeek.com/426749/how-to-access-your-linux-wsl-files-in-windows-10/)

thanks

---

### Post by jimninja on 2021-11-20
and now, someone knows the problem, It seems that I cant build an open  wrt image with the windows ubuntu terminal, everytime I get the same  error:

```
sed -i "s/Installed-Time: .*/Installed-Time: 1637254284/" /home/james/openwrt/build_dir/target-arm_cortex-a9+vfpv3-d16_musl_eabi/root-mvebu/usr/lib/opkg/status
rm -rf /home/james/openwrt/build_dir/target-arm_cortex-a9+vfpv3-d16_musl_eabi/root-mvebu/boot /home/james/openwrt/build_dir/target-arm_cortex-a9+vfpv3-d16_musl_eabi/root-mvebu/tmp/* /home/james/openwrt/build_dir/target-arm_cortex-a9+vfpv3-d16_musl_eabi/root-mvebu/usr/lib/opkg/info/*.postinst* /home/james/openwrt/build_dir/target-arm_cortex-a9+vfpv3-d16_musl_eabi/root-mvebu/usr/lib/opkg/lists/* /home/james/openwrt/build_dir/target-arm_cortex-a9+vfpv3-d16_musl_eabi/root-mvebu/var/lock/*.lock
[B]find /home/james/openwrt/build_dir/target-arm_cortex-a9+vfpv3-d16_musl_eabi/root-mvebu/ -mindepth 1 -execdir touch -hcd "@1637254284" "{}" +
find: The relative path 'Files/WindowsApps/CanonicalGroupLimited.UbuntuonWindows_2004.2021.825.0_x64__79rhkp1fndgsc' is included in the PATH environment variable, which is insecure in combination with the -execdir action of find.  Please remove that entry from $PATH
make[2]: *** [package/Makefile:73: package/install] Error 1[/B]
make[2]: Leaving directory '/home/james/openwrt'
make[1]: *** [package/Makefile:111: /home/james/openwrt/staging_dir/target-arm_cortex-a9+vfpv3-d16_musl_eabi/stamp/.package_install] Error 2
make[1]: Leaving directory '/home/james/openwrt'
make: *** [/home/james/openwrt/include/toplevel.mk:230: world] Error 2
[1]+  Done                    make download


```

---

### Post by CharlesA on 2021-11-21
You can try editing your $PATH variable and remove the windows references.

```
export PATH="/home/$USER/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin"
```

It will overwrite the $PATH variable unless you log off.

---

