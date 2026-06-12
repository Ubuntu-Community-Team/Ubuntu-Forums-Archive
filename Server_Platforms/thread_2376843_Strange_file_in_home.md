---
title: "Strange file in home"
date: 2017-11-06
forum: Server Platforms
---

### Post by dlfuller@ClientandFuller. on 2017-11-06
My username is dlfuller.  When logged in by SSH to a headless Ubuntu Server 17.04 named SERGIO, I always see this file:

```
-rw-rw-r--   1 dlfuller dlfuller  15500 Sep  6 17:17 lfuller@SERGIO:~$
```

Its name is missing the first letter of my username.

What is it?  And, is something amiss?

---

### Post by SeijiSensei on 2017-11-06
You probably accidentally copied the command prompt and created a file with the same name.  I've done that myself.  Just delete the file, and you should be fine.

---

### Post by HermanAB on 2017-11-07
If you want to know who is logged in to your machine, just run the command 'who'.  Also, do have a look at your server log files from time to time.

---

### Post by dlfuller@ClientandFuller. on 2017-12-02
Thanks guys.  I realize this is a dummie question, but it remains an annoying reminder every time I do a ls on my home directory.

rm or sudo rm does not delete this thing (file?).  who shows me properly as the current user.

Other suggestions please?

---

### Post by powersj on 2017-12-04
The following should delete the file and have you confirm that you wish to delete that specific file:

```

rm -i lfuller@SERGIO\:~\$
```

---

### Post by dlfuller@ClientandFuller. on 2017-12-05
Thanks for the suggestion powersj.

But tried it and got…
```
rm: cannot remove 'lfuller@SERGIO:~$': No such file or directory
```

---

### Post by volkswagner on 2017-12-05
Try using the tab key to complete your rm command.

Type:

```
rm lfuller
```

Then press the tab key to complete the filename.
once you are confident press enter to remove the file.

If that does not work please paste output of following command:
```
ls -al ~/
```

Obviously you'll need to be in your home directory for the tab completion to work.

---

### Post by dlfuller@ClientandFuller. on 2017-12-06
And a big thank you volkswagner!  File gone.

My tab completion command:```
rm lfuller@SERGIO\:~\$\  
```

But to continue with another dummie question, it is slightly different (adding a back slash) from what powersj had suggested and did not work:```
rm -i lfuller@SERGIO\:~\$
```

What did the tab completion actually do?

---

### Post by powersj on 2017-12-06
> **dlfuller@ClientandFuller. said:**
> 
But to continue with another dummie question, it is slightly different (adding a back slash) from what powersj had suggested and did not work:```
rm -i lfuller@SERGIO\:~\$
```

What did the tab completion actually do?

Not a dumb question :) Those backslashes are escaping special characters that the terminal would otherwise try to interpret. For example, the dollar-sign is used in shell to preface when you want to reference a variable, but putting a backslash in front of dollar-sign tells the terminal you actually mean the dollar-sign character and not some variable name.

The reason my command did not work is there was a space at the end of the filename that was not immediately apparently from the output we had. The tab completion added on a final backslash to escape that space as well allowing you to delete the actual file.

---

### Post by dlfuller@ClientandFuller. on 2017-12-06
Aha, I get it!  Okay with understanding the need to escape characters.  And now, also the importance of looking out for spaces in filenames. 

Thanks again powersj for the explanation.

---

