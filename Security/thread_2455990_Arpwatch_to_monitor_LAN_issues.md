---
title: "Arpwatch to monitor LAN issues"
date: 2021-01-01
forum: Security
---

### Post by coppolino97 on 2021-01-01
Hi all,
I have installed on a Ubuntu VirtualMachine arpwatch package.
Ubuntu version installed on this VM is Ubuntu Server 20.04 LTS
```

coppoadmin@copponetwork:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="20.04.1 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04.1 LTS"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal

```

I do not have logs about ArpWatch on this VM and I have changed some configuration as suggested here: [https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1692512.html](https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1692512.html)


After that I do not receive any mail about its activities.
I setted e-mail address inside arpwatch.conf file
```

root@copponetwork:/var/lib/arpwatch# cat /etc/arpwatch.conf
ens3 -a -n 192.168.1.0/24 -m xxxxxxxx@gmail.com

```

and ssmtp package is installed, configured. I sent mail with success using this command:
```
echo -e 'Subject: test\n\nTesting ssmtp' | sendmail -v myemailaddress@gmail.com
```

Someone can help me?
Thanks!

---

### Post by EuclideanCoffee on 2021-01-01
Where is this machine located? If it's in the cloud, you are sending from some public IP space that may be blocked by your provider. Check your spam folder. If your device is inside your LAN, then your firewall or ISP may block email functionality as this is common.

---

### Post by coppolino97 on 2021-01-02
Hi,
My machine is inside my LAN.
I have not issue about sending e-mail if I start to send it using CLI.

Thanks!

---

