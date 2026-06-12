---
title: "openssl, is this a decent level of encryption?"
date: 2021-10-16
forum: Security
---

### Post by mertnlee on 2021-10-16
Hi Folks,
I am encrypting for storage in the cloud using the following openssl command. Is this secure or can I do better with different openssl arguments?

#!/bin/bash 
#
read -p Password: password
cat $1 | openssl enc -iter 1000 -bf -salt -out $1.dat -pass pass:"$password"

Cheers,
Marty

---

### Post by CharlesA on 2021-10-16
That all depends on what you mean by "cloud." Are you uploading to S3 or another service?

---

### Post by mertnlee on 2021-10-16
By cloud I mean uploading to google drive or carrying about with me on a losable usb stick. The encryption is to protect my backups.

---

### Post by CharlesA on 2021-10-18
You can use rclone for syncing to Google Drive, but the setup process seems [pretty involved if you want encryption]("https://www.section.io/engineering-education/encrypting-gdrive-using-rclone/").

You could always encrypt the USB stick with LUKS or the like rather than try to do file level encryption. VeraCrypt might be more user friendly though.

---

