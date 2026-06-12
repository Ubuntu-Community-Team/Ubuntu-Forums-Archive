---
title: "Ubuntu  LAMP Strange Permission Problems"
date: 2006-10-27
forum: Server Platforms
---

### Post by Anapologetos on 2006-10-27
hey, thanks for taking your time to read this:
I am running an Intranet Webserver on Ubuntu Server 6.06, Default LAMP install.
Apache User = www-data
selinux = OFF
php safe mode = OFF
(The webserver is written purely in php5)
What is happening is that I am getting some really strang permission errors that I think is a config problem with ubuntu, as this is a new install (The previous installation was running on suse10 with no errors)

When a user goes to upload a file, php grabs the username and creates a folder with that name--It then goes to copy the upload file over to the newly created dir. That is when it errors out and says "Permission Denied"

I did some stat() on the directory while it was being written too -- the only
differnce between run 1 and run 2 is the "mode" of the directory.
1st Run: [mode] => 16877
2nd Run: mode] => 16895

I suspect the permissions are changing after php lets go the
directory. When I ask who owns the directory created it reports back
"root" (GUID = 0). The webserver is running as www-data, and when the final file is uploaded, it is owned by root, and has a sticky bit and suid on it for some reason. (this happens even if the dir is owned by root or www-data)


I also tryied manually setting the mode -- however I get a denied
message back: Warning: chmod() [function.chmod]: Operation not
permitted.

I have no idea if this is an ubuntu spefic problem or if it is the LAMP config.
Any ideas?

Thanks!
Anapologetos


Output:

Array ( [0] => 18 [1] => 156435 [2] => 16877 [3] => 2 [4] => 0 [5] =>
0 [6] => -1 [7] => 0 [8] => 1161300778 [9] => 1161300778 [10] =>
1161300778 [11] => -1 [12] => -1 [dev] => 18 [ino] => 156435 [mode] =>
16877 [nlink] => 2 [uid] => 0 [gid] => 0 [rdev] => -1 [size] => 0
[atime] => 1161300778 [mtime] => 1161300778 [ctime] => 1161300778
[blksize] => -1 [blocks] => -1 )
Warning: chmod() [function.chmod]: Operation not permitted in
/mnt/groups/MIS//modules/turnin/uploadhw.php on line 78
Array ( [0] => 18 [1] => 156435 [2] => 16877 [3] => 2 [4] => 0 [5] =>
0 [6] => -1 [7] => 0 [8] => 1161300778 [9] => 1161300778 [10] =>
1161300778 [11] => -1 [12] => -1 [dev] => 18 [ino] => 156435 [mode] =>
16877 [nlink] => 2 [uid] => 0 [gid] => 0 [rdev] => -1 [size] => 0
[atime] => 1161300778 [mtime] => 1161300778 [ctime] => 1161300778
[blksize] => -1 [blocks] => -1 )
Warning: copy(/www/courseware/BFF/turnin/09-08-uploadfile/user/Oct-19--18-35-39-RdrMsgSplash.pdf)
[function.copy]: failed to open stream: Permission denied in
/mnt/groups/MIS//modules/turnin/uploadhw.php on line 83
Error Uploading File



2nd time

Array ( [0] => 18 [1] => 156435 [2] => 16895 [3] => 1 [4] => 0 [5] =>
0 [6] => -1 [7] => 0 [8] => 1161300778 [9] => 1161300778 [10] =>
1161300778 [11] => -1 [12] => -1 [dev] => 18 [ino] => 156435 [mode] =>
16895 [nlink] => 1 [uid] => 0 [gid] => 0 [rdev] => -1 [size] => 0
[atime] => 1161300778 [mtime] => 1161300778 [ctime] => 1161300778
[blksize] => -1 [blocks] => -1 )
Warning: chmod() [function.chmod]: Operation not permitted in
/mnt/groups/MIS//modules/turnin/uploadhw.php on line 78
Array ( [0] => 18 [1] => 156435 [2] => 16895 [3] => 1 [4] => 0 [5] =>
0 [6] => -1 [7] => 0 [8] => 1161300778 [9] => 1161300778 [10] =>
1161300778 [11] => -1 [12] => -1 [dev] => 18 [ino] => 156435 [mode] =>
16895 [nlink] => 1 [uid] => 0 [gid] => 0 [rdev] => -1 [size] => 0
[atime] => 1161300778 [mtime] => 1161300778 [ctime] => 1161300778
[blksize] => -1 [blocks] => -1 ) Uploaded 22351 bytes in a
application/pdf-type of file

---

### Post by bache on 2006-10-31
How do you create the dirs?

Try that way:

<?php
$oldumask = umask(0);
mkdir('your_dir', 0777); 
umask($oldumask);
?>

---

### Post by Anapologetos on 2006-10-31
What a frikin' idiot I am!  ](*,) 
Thanks, that worked great! :) 
Anapologetos

---

