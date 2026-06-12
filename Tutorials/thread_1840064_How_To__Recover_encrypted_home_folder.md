---
title: "How To:  Recover encrypted home folder"
date: 2011-09-06
forum: Tutorials
---

### Post by Z3ro3X on 2011-09-06
I was searching for a way to restore an encrypted private home folder after a fresh install of Ubuntu for when new versions come out.  All the methods I found where overly complicated or not practical for my situation.  I ended up discovering my own method which is way easier.  I'm posting the solution here for any one who needs it.

When doing a fresh install and during the account creation, create an temporary account different from the one you're restoring.  If your account name was bob than create bob2.  Log on the temporary account and open Terminal from Applications -> Accessories.

Type this.  Note:  I don't normally use shell to move files/folders so if I typed something wrong feel free to correct me.  We'll assume for now that the account name you're restoring is called bob. Remember to substitute "bob" with the account name you're restoring.

sudo mv -r /home/bob /home/bob_bak
sudo mv -r /home/.ecryptfs/bob /home/.ecryptfs/bob_bak

Open Users and Groups from System -> Administration.  Click Add, enter the exact Name and Username of the account you want to restore and check box it to Encrypt it.  Make sure you use the exact same password of the original account or this wont work.  Make sure to change the account type to Administrator so you can delete your temporary account when you're done.  Close out of that window.

Go back to Terminal and type this.  Note:  Remember to substitute bob with the account name you just created.

sudo rm -r '/home/bob' '/home/.ecryptfs/bob'
sudo mv -r /home/bob_bak /home/bob
sudo mv -r /home/.ecryptfs/bob_bak /home/.ecryptfs/bob
sudo chown -R bob '/home/bob' '/home/.ecryptfs/bob'
sudo chgrp -R bob '/home/bob' '/home/.ecryptfs/bob'

You should be good to go after this.  Just log out of your temp account and into your restored account and delete the temp account.

---

