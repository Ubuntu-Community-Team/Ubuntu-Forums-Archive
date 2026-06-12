---
title: "Issue After Sending ATOP Raw Files Via HTTP POST"
date: 2014-01-09
forum: Server Platforms
---

### Post by Kirk Schnable on 2014-01-09
Hey everyone,

I wanted to come up with a way to do some accounting of what programs are being used on a large set of computers.  I decided to achieve this by using atop.  I would send the raw files to a central server, and do reporting on them later by scripting some atop -r commands and sending the output to a MySQL database.

I decided to create a small PHP API running on a web server internally to accept these raw files.

It looks like it's working great, but there's an issue with actually using the files.  When I try to use them, atop says **raw file *filename* has incompatible format**.  Unfortunately I have no way of verifying the problem, because catting an atop raw file is useless.  I get the same kind of gibberish when I cat the file on my server, so I'm not sure what's wrong. 

I'm going to go out on a limb here and say it might have something to do with the HTTP encoding of the form.  I know in the past when dealing with FTP servers, there was a "binary" and "ASCII" transfer mode, and transferring certain files with the wrong mode could corrupt them.  I'm wondering if something like this is happening here, and if I need an enctype on my post submission or something.  Is there something I'm doing wrong in the PHP handling of the file, or in the CURL uploading of the file?  I've never seen data corrupted like this by a PHP upload form.


Here's what I'm doing.

**Server API (written in PHP)**
```

<?php
// [... snip ...]
$storageDir = "/home/atoplogs/rawfiles";
// [... snip ...]
$payload = $_FILES['payload'];
// [... snip ...]
move_uploaded_file($_FILES['payload']['tmp_name'], "$storageDir/$fileID");
// [... snip ...]
?>

```

**Client (Bash Script)**
```

#!/bin/bash
# [...snip...]
curl -F "payload=@$logfile" -s "$APIURL"
# [...snip...]

```


It would be most helpful to me if someone could provide some insights on how this PHP form upload could possibly go wrong and corrupt the file, as well as any special considerations I need to take when dealing with these atop raw files...

Thanks,
Kirk

---

### Post by Kirk Schnable on 2014-01-14
Hey everyone,

I was able to resolve the issue by making a change in my client script.  I am setting the payload variable to type of application/octet-stream.

**_Old Client:_**
> **Kirk Schnable said:**
> **Client (Bash Script)**
```

#!/bin/bash
# [...snip...]
curl -F "payload=@$logfile" -s "$APIURL"
# [...snip...]

```

**_New Client:_**
```

#!/bin/bash
# [...snip...]
curl -F "payload=@$logfile;type=application/octet-stream" -s "$APIURL"
# [...snip...]

```

---

