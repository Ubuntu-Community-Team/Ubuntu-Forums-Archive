---
title: "BackupPC  $Conf{BackupFilesOnly} Problem"
date: 2008-05-30
forum: Server Platforms
---

### Post by rkulp on 2008-05-30
I am trying to backup selected files on a Windows XP box using a USB drive on my Ubuntu 8.04 computer. The backup starts but always tries to backup the entire C$ share rather than the selected files. Here are the first few lines of the Xfer Log:

Running: /usr/bin/smbclient \\\\dc6mqf61\\C\$ -U dick -E -N -d 1 -c tarmode\ full -Tc -
full backup started for share C$
Xfer PIDs are now 7929,7928
Domain=[DC6MQF61] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tarmode is now full, system, hidden, noreset, verbose

Here is the dc6mqf61.pl file with username and password changed:

$Conf{XferMethod} = 'smb';
$Conf{RsyncdUserName}='UUU';
$Conf{RsyncdPasswd} = 'PPPP';
$Conf{XferLogLevel} = 2;
$Conf{smbShareName}= ['c','d'];
#$Conf{BackupFilesOnly} = {
#	'c' => ['/ASD', '/Clients and TSEPWin Users', '/CitizensBank', '/AscendFCU', '/K&ABusinessDocuments', '/Kulp&Associates', '/USAA', '/Lions','/Visual Studio 2005','/TIAA-CREF','/WACC'],
#	'd' => ['/TSEPWin','/Generic Registration VB2005'],
#	} ;
$conf{BackupFilesOnly} = {
	'c' => ['/CitizensBank'],
	'd' => ['TSEPWin'],
	};

You can see that I had originally tried a long list of files but cut it down to just two directories to see what would happen.

I listed the directories rather than a hash since I really don't know how to do the hash. If that is the only way to get a list of directories backed up, I would appreciate instructions at the newbie level.

I'm not sure what I should have included so will gladly add additional information.

---

