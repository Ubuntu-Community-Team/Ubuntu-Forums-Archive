---
title: "Can I get help for .jar program on Ubuntuforums?"
date: 2010-10-09
forum: The Cafe
---

### Post by kagashe on 2010-10-09
I recently purchased soft copy of one Indian Standard from [Bureau of Indian Standards (BIS)]("http://www.standardsbis.in/Gemini/home/Home.action"). The downloaded standard is in pdf format and the site supplies Plug-in for Windows and Linux. The Linux plug-in installs a .jar program through which you log-in to BIS site and view the purchased standard. You have to indicate the path of downloaded standard in the plug-in. The plug-in verifies that it is the standard which you have paid for decrypts the downloaded standard and opens it in Acrobat Reader. I am facing following problems in this program:
1. If I install as normal user it fails to connect to BIS site.
2. If I install using sudo it connects to BIS site and shows the downloaded standard.
3. It also accepts the path of downloaded file but fails to open the file.
4. On closing and retrying the program fails to restart with error "Problem in preference folder path. Please select path.

Following is the log in the application:
> 8 Oct, 2010 8:12:32 PM com.bis.clientapp.EBISApplication getInstance
INFO: Viewer is created
8 Oct, 2010 8:12:33 PM com.bis.clientapp.EBISApplication addPreferencePath
INFO: Adding preference file.
8 Oct, 2010 8:12:33 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :file-path
8 Oct, 2010 8:12:33 PM com.bis.clientapp.EBISApplication loadProxySettings
INFO: Loading the stored proxy settings.
8 Oct, 2010 8:12:56 PM com.bis.clientapp.EBISApplication downloadConfigFile
INFO: Downloading the confiuration file...
8 Oct, 2010 8:12:56 PM com.bis.clientapp.EBISApplication downloadConfigFile
INFO: Proxy Details : Default System Settings.
8 Oct, 2010 8:13:03 PM com.bis.clientapp.EBISApplication extractZippedFile
INFO: Files unzipped.
8 Oct, 2010 8:13:03 PM com.bis.clientapp.EBISApplication getDataFromCSV
INFO: Getting the data from CSV file.
8 Oct, 2010 8:13:03 PM com.bis.clientapp.EBISApplication getRowCount
INFO: Getting row count from 
8 Oct, 2010 8:13:14 PM com.bis.clientapp.EBISApplication downloadConfigFile
INFO: Downloading the confiuration file...
8 Oct, 2010 8:13:14 PM com.bis.clientapp.EBISApplication downloadConfigFile
INFO: Proxy Details : Default System Settings.
8 Oct, 2010 8:13:19 PM com.bis.clientapp.EBISApplication extractZippedFile
INFO: Files unzipped.
8 Oct, 2010 8:13:19 PM com.bis.clientapp.EBISApplication getDataFromCSV
INFO: Getting the data from CSV file.
8 Oct, 2010 8:13:19 PM com.bis.clientapp.EBISApplication getRowCount
INFO: Getting row count from 
8 Oct, 2010 8:13:47 PM com.bis.clientapp.EBISApplication updateNodeData
INFO: Updating the node value :file-path
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication openStandard
INFO: Opening Standard : 14205_1
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :file-path
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication checkForDependencies
INFO: checking the dependencies for the file :14205_1
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication keyDecryptFile
INFO: Decrypting input file.
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication getKeyGeneratorvalue
INFO: Getting key generated value for the keyfile.
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication decryptFile
INFO: Decrypting the file.
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication openFile
INFO: Opening PDF file : 14205_1
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :acrobatpath
8 Oct, 2010 8:13:54 PM com.bis.clientapp.EBISApplication openFile
SEVERE: IOError occurred while opening the PDF file.Cannot run program "/home/turbine/Downloads/14205_1.pdf": java.io.IOException: error=13, Permission denied
8 Oct, 2010 8:14:51 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :file-path
8 Oct, 2010 8:14:51 PM com.bis.clientapp.EBISApplication checkForDependencies
INFO: checking the dependencies for the file :14205_1
8 Oct, 2010 8:14:51 PM com.bis.clientapp.EBISApplication keyDecryptFile
INFO: Decrypting input file.
8 Oct, 2010 8:14:51 PM com.bis.clientapp.EBISApplication getKeyGeneratorvalue
INFO: Getting key generated value for the keyfile.
8 Oct, 2010 8:14:51 PM com.bis.clientapp.EBISApplication decryptFile
INFO: Decrypting the file.
8 Oct, 2010 8:14:51 PM com.bis.clientapp.EBISApplication openFile
INFO: Opening PDF file : 14205_1
8 Oct, 2010 8:14:51 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :acrobatpath
8 Oct, 2010 8:14:51 PM com.bis.clientapp.EBISApplication openFile
SEVERE: IOError occurred while opening the PDF file.Cannot run program "/home/turbine/Downloads/14205_1.pdf": java.io.IOException: error=13, Permission denied
8 Oct, 2010 8:15:24 PM com.bis.clientapp.EBISApplication getExecutablesDialog
INFO: Setting executable file...
8 Oct, 2010 8:15:44 PM com.bis.clientapp.EBISApplication updateNodeData
INFO: Updating the node value :acrobatpath
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication openStandard
INFO: Opening Standard : 14205_1
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :file-path
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication checkForDependencies
INFO: checking the dependencies for the file :14205_1
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication keyDecryptFile
INFO: Decrypting input file.
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication getKeyGeneratorvalue
INFO: Getting key generated value for the keyfile.
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication decryptFile
INFO: Decrypting the file.
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication openFile
INFO: Opening PDF file : 14205_1
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :acrobatpath
8 Oct, 2010 8:16:14 PM com.bis.clientapp.EBISApplication openFile
SEVERE: IOError occurred while opening the PDF file.Cannot run program "/home/turbine/Downloads/14205_1.pdf": java.io.IOException: error=13, Permission denied
8 Oct, 2010 8:22:29 PM com.bis.clientapp.EBISApplication openStandard
INFO: Opening Standard : 14205_1
8 Oct, 2010 8:22:29 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :file-path
8 Oct, 2010 8:22:29 PM com.bis.clientapp.EBISApplication checkForDependencies
INFO: checking the dependencies for the file :14205_1
8 Oct, 2010 8:22:29 PM com.bis.clientapp.EBISApplication keyDecryptFile
INFO: Decrypting input file.
8 Oct, 2010 8:22:29 PM com.bis.clientapp.EBISApplication getKeyGeneratorvalue
INFO: Getting key generated value for the keyfile.
8 Oct, 2010 8:22:29 PM com.bis.clientapp.EBISApplication decryptFile
INFO: Decrypting the file.
8 Oct, 2010 8:22:29 PM com.bis.clientapp.EBISApplication openFile
INFO: Opening PDF file : 14205_1
8 Oct, 2010 8:22:29 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :acrobatpath
8 Oct, 2010 8:26:10 PM com.bis.clientapp.EBISApplication openStandard
INFO: Opening Standard : 14205_1
8 Oct, 2010 8:26:10 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :file-path
8 Oct, 2010 8:26:10 PM com.bis.clientapp.EBISApplication checkForDependencies
INFO: checking the dependencies for the file :14205_1
8 Oct, 2010 8:26:10 PM com.bis.clientapp.EBISApplication keyDecryptFile
INFO: Decrypting input file.
8 Oct, 2010 8:26:10 PM com.bis.clientapp.EBISApplication getKeyGeneratorvalue
INFO: Getting key generated value for the keyfile.
8 Oct, 2010 8:26:10 PM com.bis.clientapp.EBISApplication decryptFile
INFO: Decrypting the file.
8 Oct, 2010 8:26:10 PM com.bis.clientapp.EBISApplication openFile
INFO: Opening PDF file : 14205_1
8 Oct, 2010 8:26:10 PM com.bis.clientapp.EBISApplication getNodeValue
INFO: Getting the value of the node :acrobatpath
8 Oct, 2010 8:29:05 PM com.bis.clientapp.EBISApplication getExecutablesDialog
INFO: Setting executable file...
8 Oct, 2010 8:29:23 PM com.bis.clientapp.EBISApplication updateNodeData
INFO: Updating the node value :acrobatpath

kagashe

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-10-09
Can't you just use ubuntu's document reader? That supports pdf.

---

### Post by kagashe on 2010-10-09
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Can't you just use ubuntu's document reader? That supports pdf.The file is encrypted and won't open in any pdf reader. The plugin verifies that you are the buyer, decrypts and opens it in its own viewer using acroread in background.

kagashe

---

