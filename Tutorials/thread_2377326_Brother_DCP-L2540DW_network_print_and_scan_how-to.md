---
title: "Brother DCP-L2540DW network print and scan how-to"
date: 2017-11-11
forum: Tutorials
---

### Post by donh32 on 2017-11-11
Hi,

I was having a little trouble getting my Brother printer to work over the network with their instructions so here is my documentation.

Brother printer: DCP-L2540DW
OS: Kubuntu 16.04.2 64bit

---------------------------------------------------------------------------
**This will install the Brother printer drivers.**  
Your printer should be setup on the network and be reachable via it's web interface.

**Download the files from Brother's website:**
dcpl2540dwcupswrapper-3.2.0-1.i386.deb
dcpl2540dwlpr-3.2.0-1.i386.deb

**Install 32bit supporting libraries:**
If you run the brother setup script, you will receive an error: Package 'ia32-libs' has no installation candidate.  
It is not available for 16.04 so you need to install the replacements before running the script:
sudo apt-get install lib32z1 lib32ncurses5

**Install the files:**
sudo dpkg -i dcpl2540dwcupswrapper-3.2.0-1.i386.deb
sudo dpkg -i dcpl2540dwlpr-3.2.0-1.i386.deb

You will now have a populated /opt/brother/Printers directory

**Open a browser and go to the CUPS printer interface:**
[http://localhost:631](http://localhost:631)

**Setup printer in CUPS:**
Click on Administration at the top
Click on the Add Printer button
Enter your username and password
Under Other Network Printers, choose Internet Printing Protocol (http), click Continue
Under Connection enter YOUR printer's information,  [http://192.168.1.10:631](http://192.168.1.10:631)  then click Continue
Enter the printers name.  Note that you cannot use spaces in the name.
For a Make of the printer click Brother, click Continue
Find the driver for the correct model and click Add Printer 
You can now print a test page: Maintenance menu > Print Test Page

---------------------------------------------------------------------------
**This will install the Brother scanner software:**

**Download the files from Brother's website:**
brscan4-0.4.4-4.amd64.deb

**Install the files:**
sudo dpkg -i brscan4-0.4.4-4.amd64.deb

**You will now have a populated scanner directory to change to:**
cd /opt/brother/scanner/brscan4

**Figure out information for scanner setup:**
USAGE: brsaneconfig4 [-OPTION]   OPTION:                                                                                             
       -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx                                                                         
       -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx                                                                     
                   : Add network scanner                                                                                             
       -r FRIENDLY-NAME [FRIENDLY-NAME ...]                                                                                          
                   : Remove network scanner                                                                                          
       -d          : Diagnosis                                                                                                       
       -p          : Ping (for network scanners)                                                                                     
       -s:[LABEL]  : Save current configuration                                                                                      
       -l:[LABEL]  : Load saved configuration                                                                                        

**Run the executable setup files:**
sudo ./brsaneconfig4 -a name=Brother_DCP-L2540DW model=DCP-L2540DW ip=192.168.1.10
sudo ./setupSaneScan4

**Test scanning with a program:**
skanlite (if running Kubuntu)

---

