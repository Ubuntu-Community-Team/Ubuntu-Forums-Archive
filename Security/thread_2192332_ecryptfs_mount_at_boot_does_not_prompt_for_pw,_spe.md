---
title: "ecryptfs mount at boot does not prompt for p/w, specifies disk not avai"
date: 2013-12-07
forum: Security
---

### Post by helloworld1215 on 2013-12-07
/root/.crypt /root/crypt ecryptfs ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=d395309aaad4de06,ecryptfs_fnek_sig=d395309aaad4de06 0 0

I have the above in fstab. It is specifying that the /root/crypt disk is not available. However, it does not offer the option to wait or resolve manually. It simply continues on with the boot. In addition there is no mention of this occurring in /var/log/boot.log. 

My intention is to decrypt ecryptfs at boot (not dm_crypt), not pam login as provided by the ecryptfs private utils. I am aware of the functionality provided by dm_crypt/ecryptfs at user login.

/root/crypt is on a mount that is specified before in /etc/fstab and is successfully mounted.

---

