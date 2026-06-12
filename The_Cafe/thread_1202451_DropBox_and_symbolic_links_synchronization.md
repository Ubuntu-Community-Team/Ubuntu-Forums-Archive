---
title: "DropBox and symbolic links synchronization"
date: 2009-07-02
forum: The Cafe
---

### Post by legolas_w on 2009-07-02
Hi
Thank you for reading my post.
Is there anyone here who use tip explained here: [http://lifehacker.com/5154698/sync-files-and-folders-outside-your-my-dropbox-folder](http://lifehacker.com/5154698/sync-files-and-folders-outside-your-my-dropbox-folder) to sycnhronize files and folders outside the dropbox folder?

I am wondering whether I can for example synchronize my songbird db using this trick or not.

Thanks.

---

### Post by hydrox24 on 2012-01-30
For the sake of those who stumble onto this thread:

I do use symbolic links with dropbox and this worked well for a long while when I had dropbox inside my ntfs formatted data partition. However I now have a ext3 formatted Data partition and of course on of the major differences for this is file permissions.
When linking files into dropbox (eg linking /home/$USER/Documents/foo_bar.jpg /media/Data/Dropbox) I now get consistent issue with dropbox being locked down and just haveing permissions trouble in general. I would recommend that you make sure dropbox is in a filesystem without permissions if you wish to make use of soft linking as it will make life significantly easier.

These four commands will unlock your dropbox if you are haveing issues (but only until a reboot)

sudo chown -R $USER /path/to/dropbox
sudo chmod -R u+rw /path/to/dropbox
sudo chown -R $USER ~/.dropbox
sudo chmod -R u+rw ~/.dropbox

Hope this helps any passers-by. Any permanent and solid (non-hacky) solutions would be wonderful too if anyone has any idea.

---

