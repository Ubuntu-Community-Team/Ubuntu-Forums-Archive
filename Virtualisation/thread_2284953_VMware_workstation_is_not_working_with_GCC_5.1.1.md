---
title: "VMware workstation is not working with GCC 5.1.1"
date: 2015-07-02
forum: Virtualisation
---

### Post by Ebram_Shehata on 2015-07-02
[CENTER][COLOR=#2f4f4f][B][FONT=Ubuntu]after installing ubuntu 15.04 vmware is no longer working with gcc 5.1.1[/FONT]
[FONT=Ubuntu]while trying to launch vmware workstation ...[/FONT]
[FONT=Ubuntu]pic : 

[/FONT][IMG]http://www.promisr.net/uploads/1435843657452.png[/IMG]

[FONT=Ubuntu]tried to push refresh , nothing happens .. also tried to add this path[/FONT]
[FONT=Ubuntu]/usr/lib/gcc/[/FONT]
[FONT=Ubuntu]and any sub-path but nothing :([/FONT]
[FONT=Ubuntu]i tried applying these :

```

curl http://pastie.org/pastes/9934018/download -o /tmp/vmnet-3.19.patch
cd /usr/lib/vmware/modules/source
tar -xf vmnet.tar
patch -p0 -i /tmp/vmnet-3.19.patch
mv vmnet.tar vmnet.tar.SAVED
tar -cf vmnet.tar vmnet-only
rm -r vmnet-only
vmware-modconfig --console --install-all

```[/FONT]

but i got error : 

[PHP]root@ebram96:~# curl http://pastie.org/pastes/9934018/download -o /tmp/vmnet-3.19.patch
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1026    0  1026    0     0     39      0 --:--:--  0:00:25 --:--:--   233
root@ebram96:~# cd /usr/lib/vmware/modules/source
root@ebram96:/usr/lib/vmware/modules/source# tar -xf vmnet.tar
root@ebram96:/usr/lib/vmware/modules/source# patch -p0 -i /tmp/vmnet-3.19.patch
patch unexpectedly ends in middle of line
patch: **** Only garbage was found in the patch input.
root@ebram96:/usr/lib/vmware/modules/source# mv vmnet.tar vmnet.tar.SAVED
root@ebram96:/usr/lib/vmware/modules/source# tar -cf vmnet.tar vmnet-only
root@ebram96:/usr/lib/vmware/modules/source# tar -cf vmnet.tar vmnet-only
root@ebram96:/usr/lib/vmware/modules/source# vmware-modconfig --console --install-all
Failed to get gcc information.[/PHP][/B][/COLOR][/CENTER]

---

### Post by Ebram_Shehata on 2015-07-05
no ideas ? ! :'(

---

### Post by Ebram_Shehata on 2015-07-19
I did it by downgrading GCC in my Ubuntu here it is ..
1 - Uninstall GCC 5.1.1 :


    ```
sudo apt-get remove gcc-5
sudo apt-get remove --auto-remove gcc-5
sudo apt-get purge gcc-5
```


2 - install gcc 4.9.2


    ```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get install g++-4.9
```


3 - make a link to your gcc 4.9.2

```

ln -s /usr/bin/gcc-4.9 /usr/bin/gcc
ln -s /usr/bin/g++-4.9 /usr/bin/g++
```


4 - open VMware and it will run perfectly ;)

---

