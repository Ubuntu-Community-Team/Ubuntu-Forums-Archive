---
title: "Comparing File Sizes"
date: 2008-10-11
forum: Server Platforms
---

### Post by etechship on 2008-10-11
I currently have this in a bash file named test.sh

```

##get file size for every file that is in the /uploads directory
for file in `find /root/upload/ -name *.flv`; do
        localSize=`stat $file -c %s`

        newFileUser=`echo $file | cut -d/ -f4`
        newFileName=`echo $file | cut -d/ -f5`

        oDomain="http://hg.server.ucstreaming.net/~ucstream/";
        oFile="streamVids.php?test=1&file=$newFileUser/$newFileName";
        oUrl=$oDomain$oFile

        wget -q $oUrl -O /root/vids5.txt
        while read line
        do
                if [ $line != "" ]; then
                     remoteSize = $line
                fi
        done < /root/vids5.txt
        rm /root/vids5.txt

        echo $localSize - $remoteSize
done

```

_**What you might need to know:**_
- I am trying to compare the file size on the local server to that the remote server.
- I have a php script that will spit out the file size for you (which is what I am wgetting above)
- I have a file named abi/f82f3568b4fea5321b97eb1245837bcd.flv that is 534897306 bytes. (and fill free to use this as a test).
- I have users and videos. I asign each video a md5 of their title, id, username, etc... (so, like the video above, the file path would be /root/upload/abi/f82f3568b4fea5321b97eb1245837bcd.flv; all the videos on the local server will always have the format /root/upload/*username*/*md5 flv file*.flv)
- This is the link to get the file size for the example video: [http://hg.server.ucstreaming.net/~ucstream/streamVids.php?test=1&file=abi/f82f3568b4fea5321b97eb1245837bcd.flv]("http://hg.server.ucstreaming.net/~ucstream/streamVids.php?test=1&file=abi/f82f3568b4fea5321b97eb1245837bcd.flv")
_**What I know:**_
- I can see the /root/vids5.txt when I comment out the rm line, and it looks correct. (it is just supposed to display the size of the file in bytes)
- I tried chmod 777 and 775 (thinking permission might be), but that didnt help

thanks for your help, and if you need anymore information, just let me know.

---

