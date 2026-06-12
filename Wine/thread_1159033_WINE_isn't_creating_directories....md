---
title: "WINE isn't creating directories..."
date: 2009-05-14
forum: Wine
---

### Post by spiney_norm on 2009-05-14
I just installed WINE and running winecfg gives me this:

```
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3
err:process:init_windows_dirs directory L"C:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"C:\\windows\\system32" could not be created, error 3

```
If anyone knows how to help, or can direct me to where I can get help, it would be greatly appreciated.

Edit: ran 
```
mv ~/.wine{,.backup} 
wineprefixcreate 

``` 
and it works now. Fallout here i come!

---

### Post by hikaricore on 2009-05-14
You didn't do something stupid like run WINE with sudo did you?

Run this:
> sudo chown username:username -R ~/.wine

Replacing username with your actual username.

---

### Post by spiney_norm on 2009-05-14
I installed wine forever ago and may have done that then. But I fixed my problems so no worries.

---

