---
title: "Administrative Tasks and Executable Bit"
date: 2010-07-05
forum: Security
---

### Post by bubufant on 2010-07-05
1. Is there a way to replace the password prompt for administrative tasks with a simple yes/no prompt like windows uac does?
Typing my password once when logging in or when unlocking the screensaver seems enough authentication to me.

2. Can i run files without executable bit? e.g. "xx might be dangerous, run anyway Yes/No?"

---

### Post by Bachstelze on 2010-07-05
> **bubufant said:**
> 1. Is there a way to replace the password prompt for administrative tasks with a simple yes/no prompt like windows uac does?

No.

> **bubufant said:**
> 2. Can i run files without executable bit? e.g. "xx might be dangerous, run anyway Yes/No?"

No.

---

### Post by teh_drizzle on 2010-07-05
Bachstelze is right, but I'd like to add that you can simulate the yes/no prompt (if all you want to add is a little reminder to yourself).

Step 1: save this as ~/yesno.sh
```
#!/bin/bash

echo -n "Do you really want to do that? [y,n]: "
read choice

if [ "$choice" = "y" ]; then
	$@
fi
```

Step 2: 
```
alias sudo="sudo ~/yesno.sh"
```

Step 3: Enable password-less sudo for your account. 

Now you've replaced the password with a yes/no prompt. :P Although I would not suggest doing this, it's not even close to simulating an OS security control. (As I said in the beginning, it's the same as a password-less prompt, no UAC, and a simple reminder.)

---

