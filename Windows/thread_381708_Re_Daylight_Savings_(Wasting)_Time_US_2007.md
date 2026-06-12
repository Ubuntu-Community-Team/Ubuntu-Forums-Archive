---
title: "Re: Daylight Savings (Wasting) Time US 2007"
date: 2007-03-10
forum: Windows
---

### Post by FLPCGuy on 2007-03-10
For those who must still use XP or 2000, here's how to get ready for the new US Daylight Saving(s) Times in 2007, first Microsoft's explanation for 2000, then my simplified directions for XP.  

 **[http://support.microsoft.com/kb/914387/en-us](http://support.microsoft.com/kb/914387/en-us)**
  **How to configure daylight saving time for the United States in 2007**

  **Important** Before you make any changes to the time zone settings, export the registry keys that are used for Windows time zones. Then, you can restore the time zone registry keys to their original state if it is necessary. To export the registry keys that used for Windows time zones, follow these steps:
          1. Click **Start**, click **Run**,   type regedit, and then press ENTER.
             2. Locate and then click the following registry key:
   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows   NT\CurrentVersion\Time Zones
             3. On the **File** menu, click **Export**.
             4. In the **File name** box, type OriginalTZDatabase.reg, and then click **Save**.
             5. Locate and then click the following registry key:
   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation
             6. On the **File** menu, click **Export**.
             7. In the **File name** box, type OriginalTZInfo.reg, and then click **Save**.
        To import the registry keys to restore the default values, follow these steps:
          1. Click **Start**, click **Run**,   type notepad, and then press ENTER.
             2. On the **File** menu, click **Open**.
             3. In the **Files of type** box, click **All   Files**.
             4. Locate where you saved the OriginalTZDatabase.reg file,   and then click **Open**.
             5. Copy and paste the following line to the beginning of the   file immediately after the line **Windows Registry Editor Version 5.00**:
   [-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones]   **Note **The minus sign at the beginning of this   registry key name causes the deletion of this registry key and all its   subkeys. The import process then uses the rest of the file to re-create the   registry key and to populate it with the default values. For example, the   beginning of the file should resemble the following:
   Windows Registry Editor Version 5.00 [-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones]           6.
         On the **File** menu, click **Save**.
             7. In the **Save as type** box, click **All   Files**.
             8. Click **OriginalTZDatabase.reg**, and then   click **Save**.
             9. Click **Yes** when you are prompted to   replace the file.
             10. Repeat the previous steps for the OriginalTZInfo.reg file.   In step 5, add the following line to the beginning of the file immediately   after the line **Windows Registry Editor Version 5.00**:
   [-HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]   **Note **For example, the beginning of the file should   resemble the following:
   Windows Registry Editor Version 5.00 [-HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]

11. To import the registry files, follow these steps:
                 a. Click **Start**, click **Run**,     type cmd, and then press ENTER.
                       b. Type the following command, and then press ENTER:
     Regedit /s OriginalTZDatabase.reg_Path
     **Note **In this command, OriginalTZDatabase.reg_Path     represents where the OriginalTZDatabase.reg file is located.
                       c. Type the following command, and then press ENTER:
     Regedit /s OriginalTZInfo.reg_Path
     **Note **In this command, OriginalTZInfo.reg_Path     represents where the OriginalTZInfo.reg file is located.
               
             12. Restart the computer.
         
  [**For Windows 2000**, download the TZEDIT.exe utility [http://download.microsoft.com/download/5/8/a/58a208b7-7dc7-4bc7-8357-28e29cdac52f/tzedit.exe](http://download.microsoft.com/download/5/8/a/58a208b7-7dc7-4bc7-8357-28e29cdac52f/tzedit.exe)  and create a New (bogus) time zone with GMT offset, DST start and end dates that match your time zone and the DST specified in the US Energy Conservation Act of 2005 (Start DST 2 a.m. 3/11/07 three weeks early, end 11/02/07 one week later than normal) unless you live in Arizona or Mexico.
   
  **Windows 98** users&#8230;you are on your own. (Wake up and install a safe OS.)
  For Server 2003, **XP**, and 64-bit XP, see the link at [http://support.microsoft.com/kb/931836/](http://support.microsoft.com/kb/931836/)  and follow the M$ game described below the following two examples for Win2k.]
   
  **Manually configure daylight saving time dates by modifying an existing time zone**

To manually modify time zone settings by using the Time Zone Editor, follow these steps:
          1. Start Time Zone Editor.
             2. In the **Time Zones** list, select a time zone,   and then click **Edit**. For example, click **(GMT-08:00)   Pacific Time (US & Canada);   Tijuana**,   and then click **Edit**.
             3. In the **Edit Time Zone** dialog box, click   to select the **Automatically set Daylight Saving Time** check   box.
             4. Specify the correct daylight saving time start date and   end date. To do this, follow these steps:
                 a. In the **Start Day** box, click the number     of the day, the corresponding day of the week, and the month that you want.     For example, click **Second**, click **Sunday**,     and then click **March**.
                       b. Select the time that you want to start daylight saving     time. For example, select **2:00 A.M.**
                       c. In the **Last Day** box, click the number     of the day, the corresponding day of the week, and the month that you want.     For example, click **First**, click **Sunday**,     and then click **November**. 
                       d. Select the time that you want to end daylight saving     time. For example, select **2:00 A.M.**
                       e. In the **Daylight Bias** list, select how     long you want the time to change when daylight saving time is in effect.     For example, to set the clock forward 1 hour, leave the default setting of **+1:00**.
                       f. Click **OK**.
                       g. Select another time zone that has changed, and then repeat     steps a-e. For more information about the time zones that have changed,     click the following article number to view the article in the Microsoft     Knowledge Base: 
     [931836]("http://support.microsoft.com/kb/931836/") ([http://support.microsoft.com/kb/931836/](http://support.microsoft.com/kb/931836/)) February 2007     cumulative time zone update rollup for Microsoft Windows operating systems 
     Repeat steps a through f for every time zone that has     changed. When you have finished, click **Close**.
                       h. Click **Start**, point to **Settings**,     point to **Control Panel**, and then double-click **Date/Time**.
                       i. Click the **Time Zone** tab.
                       j. Select a different time zone than the **(GMT-08:00)     Pacific Time (US & Canada);     Tijuana**     time zone, and then click **Apply**.
                       k. Click **(GMT-08:00) Pacific Time (US & Canada); Tijuana**, and then click **OK**.
    
    **Note** Steps j and k are required for the new changes to take effect.
               
  In this example, steps a through f update the time zone database. Steps h through k force Windows to read the time zone database and copy the updated information into the TimeZoneInformation registry key in the current control set.
  **Manually configure daylight saving time dates by adding a new time zone**

**To manually add a new time zone by using the Time Zone Editor**, follow these steps:
          1.Start Time Zone Editor.
             2. Click **New**. In the **Time Zone Name**   box in the **Edit Time Zone** dialog box, type the time zone   name in the following format:
   (GMT +/- 0x:00) TimeZone DisplayName
   For example, type (GMT-10:00)   MyCountry1, MyCity1, MyCity2.
  
  **Note** The maximum number of characters that you can type for the time   zone name is 63 characters.
             3. In the **Abbreviation** box, type the common   name for the time zone. For example, type MyCountry   Time Zone.
             4. In the **Offset from GMT** box, select the   appropriate offset from GMT time. 
             5. Click to select the **Automatically set Daylight   Saving Time** check box. 
             6. Specify the correct daylight saving time start date and   end date. To do this, follow these steps:
                 a. In the **Start Day** box, click the number     of the day, the corresponding day of the week, and the month that you want.     For example, click **Second**, click **Sunday**,     and then click **March**. 
                       b. Specify the time that you want to start daylight saving     time. For example, select **2:00 A.M**. 
                       c. In the **Last Day** box, click the number     of the day, the corresponding day of the week, and the month that you want.     For example, click **First**, click **Sunday**,     and then click **November**. 
                       d. Specify the time that you want to end daylight saving     time. For example, select **2:00 A.M**. 
                       e. In the **Abbreviation** box at the bottom     of the **Edit Time Zone** dialog box, type the name that you     specified in step 3 
                       f. In the **Daylight Bias** box, specify how     long that you want the time to change when daylight saving time is in     effect. For example, to set the clock forward by 1 hour, leave the default     setting of **+1:00**. 
                       g.  Click **OK**. 
                       h. Click **Start**, point to **Settings**,     point to **Control Panel**, and then double-click **Date/Time**.     
                       i. Click the **Time Zone** tab.
                       j. Select the new time zone you created, and then click **Apply**.
               
         
  **XP Daylight Savings Time Patch US 2007 (revised)**
   
  [Apparently, M$ couldn't deploy the US Daylight Savings Time patch via automatic updates (as if they didn&#8217;t know which IP ranges were from US ISP&#8217;s).  M$ is taking this opportunity to harass XP users and try to entice them into downloading the MSN Spyware toolbar. The link to download the patch is shown below along with the explanation on how to follow the ridiculous and annoying procedures M$ makes it's customers endure.]
   
  Just to be an extra pain, M$ requires you to authenticate your copy of XP in order to obtain the US 2007 DST patch (revised since Nov06).  Click on the link below, then on CONTINUE VALIDATION REQUIRED, but then DON'T take the default action which is to install the MSN IE Toolbar (this is Spyware!).  Instead, scroll down the page and **_select the ALTERNATE VALIDATION METHOD_** then Continue to download and RUN a 1.4MB temporary program (GenuineCheck) that will generate a validation key from your XP license key.  Press the button to Copy the displayed key to the clipboad, then PASTE (CTRL+V or Edit,Paste) it into item 2. on the webpage and press Validate to verify that you have a licensed copy of XP and take you to the page to download the 0.5 MB DST patch. Download and Run it to set XP and Outlook 2007 DST dates.
   
  start here:
  [http://support.microsoft.com/kb/931836/](http://support.microsoft.com/kb/931836/)
   
  If this doesn't work, try Start, Settings, Control Panel, Date & Time.  Adjust the time forward one hour on Sunday 3/11/07 (3 weeks early) or later then on the Time Zone tab, **uncheck** the box for automatic Daylight Time adjustment.  In the Fall (Sunday Nov 4, one week  [COLOR=red]AFTER[/COLOR] the usual end of DST), adjust the time back one hour.  *This is the energy solution prescribed by the US Energy Conservation Act of 2005 but ignored by Mexico and Arizona.  Canada is complying to avoid confusion. *
   
  Don't forget to send M$ a bill for your time and trouble.   Don't you just love Ubuntu!

---

