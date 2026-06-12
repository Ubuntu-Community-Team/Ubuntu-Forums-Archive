---
title: "WINEDEBUG has found an issue that I can't handle"
date: 2010-12-23
forum: Wine
---

### Post by XEtedBear on 2010-12-23
In attempting to run the application '3D Home Architect V.8' under Wine (1.3.9) I found a problem with the main menu items drop down not working. I followed the WineHQ FAQ guidance and ran with WINEDEBUG=+loaddll. All the dlls loaded without problem (99% of them builtin), but two errors appeared in the WINEDEBUG output:
```

err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/tony/.local/share/mime/packages/x-wine-extension-/bzw.xml
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/tony/.local/share/applications/wine-extension-/bzw.desktop"

```

Aside from the apparent absence of a further 3 or 4 characters after the string '-extension-' in the above file names, I cannot see or understand any reason for these write failures - because my knowledge of Linux is insufficient. Can somebody give me some clues of where to look?

---

