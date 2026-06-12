---
title: "morrowind in wine...."
date: 2009-01-07
forum: Wine
---

### Post by ulyanov on 2009-01-07
im trying to install morrowind using wine, and am encountering a problem. 
i go to the terminal and type

cd /media/cdrom 
wine setup.exe 

then install shield wizard launches and  i get the error the installshield engine (ikernel.exe) could not be launched (0x8002802b)
and in the terminal it says 

err:ole:init_proxy_entry_point GetFuncDesc 8002802b should not fail here.
err:ole:proxy_manager_create_ifproxy Could not create proxy for interface {91814ebf-b5f0-11d2-80b9-00104b1f6cea}, error 0x8002802b
err:ole:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x8002802b
fixme:ole:CoCreateInstance no instance created for interface {91814ebf-b5f0-11d2-80b9-00104b1f6cea} of class {91814ec0-b5f0-11d2-80b9-00104b1f6cea}, hres is 0x8002802b

---

### Post by ulyanov on 2009-01-10
i resorted to installing xp to play this game. so bump for the help

---

### Post by 0bso on 2009-01-10
Did you try installing it via [PlayOnLinux](www.playonlinux.com)? It has morrowind listed so it should take care of any tweaking that needs to be done to install it.

---

### Post by S0m3th1ngw13rd on 2009-01-20
Also tried installing Morrowind using 
```
wine /media/cdrom/setup.exe
```

and get the following

```
err:ole:init_proxy_entry_point GetFuncDesc 8002802b should not fail here.
err:ole:proxy_manager_create_ifproxy Could not create proxy for interface {91814ebf-b5f0-11d2-80b9-00104b1f6cea}, error 0x8002802b
err:ole:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x8002802b
fixme:ole:CoCreateInstance no instance created for interface {91814ebf-b5f0-11d2-80b9-00104b1f6cea} of class {91814ec0-b5f0-11d2-80b9-00104b1f6cea}, hres is 0x8002802b

```

Anyone have a idea what this means?

Intrepid Ibex 64 bit

---

