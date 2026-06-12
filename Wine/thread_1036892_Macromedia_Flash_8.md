---
title: "Macromedia Flash 8"
date: 2009-01-11
forum: Wine
---

### Post by koolcracker on 2009-01-11
Okay, so I'm not sure whether this is a flash issue or a wine issue, but it gets part way through the installation loading, then when it goes to actually copy the files, it just closes, and pops up the next windows saying that the installation could not be completeld. Every time I've tried to isntall a program it has worked before, including flash on my old ubuntu install. I got this terminal output, although I'm not sure if it will be of use:
```
fixme:advapi:CheckTokenMembership ((nil) 0x145840 0x33e794) stub!
fixme:advapi:LookupAccountNameW (null) L"graeme" (nil) 0x33e228 (nil) 0x33e22c 0x33e220 - stub
fixme:advapi:LookupAccountNameW (null) L"graeme" 0x14de48 0x33e228 0x14e940 0x33e22c 0x33e220 - stub
err:ole:init_proxy_entry_point GetFuncDesc 8002802b should not fail here.
err:ole:proxy_manager_create_ifproxy Could not create proxy for interface {ff9f015d-973a-47e9-8857-efbd6c08a318}, error 0x8002802b
err:ole:CoUnmarshalInterface IMarshal::UnmarshalInterface failed, 0x8002802b
fixme:ole:CoCreateInstance no instance created for interface {ff9f015d-973a-47e9-8857-efbd6c08a318} of class {9c0ba3c1-2b67-45eb-bf69-bed9658d28d2}, hres is 0x8002802b
err:ole:init_proxy_entry_point GetFuncDesc 8002802b should not fail here.
err:ole:proxy_manager_create_ifproxy Could not create proxy for interface {ff9f015d-973a-47e9-8857-efbd6c08a318}, error 0x8002802b
err:ole:ClientIdentity_QueryMultipleInterfaces Failed to get pointer to interface {ff9f015d-973a-47e9-8857-efbd6c08a318}
err:msi:ITERATE_Actions Execution halted, action L"ISStartup" returned 1603

```

I heard that there is a problem with the installshield in wine 1.1.12, but I am only using 1.0.

---

### Post by yue232qi121 on 2009-01-11
is [aoc power leveling](http://www.aoc-power-leveling.org) and [age of conan power leveling](http://www.aoc-power-leveling.org) the same mean??

---

