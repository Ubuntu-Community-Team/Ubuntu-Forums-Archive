---
title: "Make sure Cron job copies files correctly"
date: 2010-07-01
forum: Server Platforms
---

### Post by Saorex on 2010-07-01
Hi guys. I made a Bash script that is fired by a Cron job every morning. It dumps an SVN backup on some Samba shared drive. I would like to know how I can make sure the job worked correctly without having to verify the shared drive every morning.

Right now, I take the job's output, save it to a log file and send this file by email. But the ouput isn't so great.

On success I get:
```
svn_flex-20100701.dump
svn_web-20100701.dump
`svndata-20100701.tgz' -> `/media/windows_shares/backup3/'
removed `svndata-20100701.tgz'
```

And on failure I get:
```
svn_flex-20100701.dump
svn_web-20100701.dump
`svndata-20100701.tgz' -> `/media/windows_shares/backup/'
```

The output comes from those lines:
```
# Tar compress all dump files into a single tgz file with the date in its name
TAR_FILENAME=svndata-$(date +%Y%m%d).tgz
tar -zcvf $TAR_FILENAME *.dump

# Move the tar file to a Windows shared drive
mv -v $TAR_FILENAME /media/windows_shares/backup/
```

Any idea how I could get a better output? It's not even telling me why the mv command fails when it does.

Thanks a lot!

---

### Post by jm2 on 2010-07-02
I have an idea to change your script. Feel free to change to meet your needs.

1. do a copy instead of the move
(A diff compares the the 2 files and give a summary if different)
2. then is it possible to do a diff on the 2 files
3. Run a script to check the script : if they match delete the file,
 if it doesn't .. give error of some sorts.

cp file.tar  ->windows
diff file.tar  -> windows >checkfile
run the below script file  output to your log file.


in a separate script file:
FILEA="checkfile"
if [ -s "$FILEA" ]; then
    echo " error file lengh doesn not match"
else
    echo "zero file length .. done successful"
    rm file.tar
fi

the -s looks at the file size of what the value in FILEA is.
Watch the spaces on the if line... it needs to match above otherwise it won't run.

Hope this helps.

---

### Post by Saorex on 2010-07-05
Not a bad idea at all. I see one problem with the way I do things. If the mount fails, I think the copy still works as it's copied to the local folder instead. So a diff won't see the difference because the file will exist. I might have to use scp instead of mounting the Samba drive and do a simple copy, and then use sdiff.

I'll do some tests during the week. Thanks!

---

