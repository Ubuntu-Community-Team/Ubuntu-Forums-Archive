---
title: "Scripting Rsync and Virsh"
date: 2012-09-07
forum: Server Platforms
---

### Post by LordVaderXIII on 2012-09-07
Hi Guys

Im having trouble scripting. I have never done scripting before and need desperately to get this going. 

I need to run the following commands in a script and then in a cron job.

virsh suspend "VM"

rsync --inplace ~/"vm disk" ~/NAS

virsh resume "VM"

Can anyone help please?

---

### Post by HugoSerrano on 2012-09-07
nano script.sh
Place the commands inside the file

```

#!/bin/bash

virsh suspend "VM"

rsync --inplace ~/"vm disk" ~/NAS

virsh resume "VM"

exit 0

```give execute permission
chmod +x script.sh

---

### Post by LordVaderXIII on 2012-09-07
> **HugoSerrano said:**
> nano script.sh
Place the commands inside the file

```

#!/bin/bash

virsh suspend "VM"

rsync --inplace ~/"vm disk" ~/NAS

virsh resume "VM"

exit 0

```give execute permission
chmod +x script.sh

Thank you very much. I turns out i was quite close. 

I missed the "exit 0" bit and i should not have created it on windows first. 

But its working correctly thank you.

---

