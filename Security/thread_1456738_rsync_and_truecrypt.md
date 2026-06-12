---
title: "rsync and truecrypt"
date: 2010-04-17
forum: Security
---

### Post by ub804 on 2010-04-17
Just for any others searching here for the wealth of knowledge :)

In reference to the posts from 2007 below, you may want to look into the "timestamp" aspect of the container mount options.  This will probably avoid having to use --checksum ;)

 - - - - - - - original posts follow - - - - - - - 

                                  **backing up truecrypt drive with rsync**             
                                                                I've had rsync  setup correctly for ages to backup my /home to an external disk, but I  recently started using truecrypt to create an encrpyted file which I  then mount as a drive (so its not a hidden volume in truecrypt)

problem is that rsync doesn't seem to notice that the encrypted file  (containing my encrypted directory) has changed, so it doesn't update  it. .... i'm assuming this is because of the security of truecypt that  it doesn't show when the file was last modified. 

any ideas how to overcome this?
maybe id just have to manually specify it to write that file each time?
                                                                                                                                                                                                                           PetePete                               December 3rd, 2007                                                                       #[**2**]("http://ubuntuforums.org/showpost.php?p=3886413&postcount=2")                                                                                  [PetePete]("http://ubuntuforums.org/member.php?u=207656")                                               
              Ubuntu Extra Shot
             [IMG]http://ubuntuforums.org/images/rank_4.png[/IMG]
                                                           
                Join Date: Dec 2006
                 Location: UK
                                            Beans: 365                 
                    Kubuntu 7.04 Feisty Fawn                                                                                          
             
                                                                                                   **Re: backing up truecrypt drive with rsync**             
                                                                doesn't  matter... found the answer (after looking for F***ing ages, make a post,  then i stumble accross it, typical!)

for anyone else looking at this, ..
you need to use the --checksum option (-c flag) takes a LOT longer, but  needed to termine if the truecrypt volume has changed.. so prob better  to have 2 rsync commands, one which does the main drive, then one which  does the folder containing truecrypt drives.

---

### Post by HermanAB on 2010-04-18
The encrypted file time and size never changes.  Therefore you need to omit the -u (update) option when using rsync on these type of files.

---

