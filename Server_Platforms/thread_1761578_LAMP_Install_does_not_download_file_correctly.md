---
title: "LAMP Install does not download file correctly"
date: 2011-05-18
forum: Server Platforms
---

### Post by rick7423 on 2011-05-18
Good day all! I do not know if this is the correct place for this, so I am going to just post and hope for the best. If it needs moved to another forum, please do so.

We have a new Ubuntu server running the latest LAMP installation (Apache2, PHP 5.3, MySQL 5.1.54 et all...).

I have a php web app that will create an Excel file successfully that I need to do a force download the the client. I have tested this code on my local machine (dev studio) and it works correctly, but when I publish that code to the new Ubuntu server, the download does not work as expected. What happens is the Excel data is displayed in the window of the browser. 

At this point I am not sure if this is something that needs to be setup in Apache2, the PHP INI file, or if the declarations in the PHP are just crap and need to be scrapped. The output file name will be of the form:'file.xls'. 

In the /etc/mime.type file, the default setting of: application/vnd.ms-excel has attributes of xls, xlb, clt, which should be OK.

I am using the following header declarations in my PHP file:

[PHP]
function save($filename, $download=false, $download_filename="")
    {
        if (!$download)
        {
            return $this->domXML->save($filename);
        }
        elseif ($this->domXML->save($filename))
        {
            $realFileInfo = $_SERVER['DOCUMENT_ROOT'].'/truck/admin/export/'.$download_filename; 
            ob_end_clean();
            // fix for IE catching or PHP bug issue 
            header("Pragma: public"); 
            header("Expires: 0"); // set expiration time 
            header('Last-Modified: '.gmdate('D, d M Y H:i:s') . ' GMT'); 
            header('Cache-Control: no-store, no-cache, must-revalidate');     // HTTP/1.1
            header('Cache-Control: pre-check=0, post-check=0, max-age=0');    // HTTP/1.1
            header ("Pragma: no-cache"); 
            
            // browser must download file from server instead of cache 
            // force download dialog 
            header("Content-Type: application/force-download"); 
            header("Content-Type: application/octet-stream");
            header('Content-Type: application/vnd.ms-excel;');                 // This should work for IE & Opera  
            header("Content-type: application/x-msexcel");
            header("Content-Type: application/download"); 
            
            // use the Content-Disposition header to supply a recommended filename and  
            // force the browser to display the save dialog.
            header("Content-Disposition: attachment; filename=".$realFileInfo.";"); 
            header("Content-Transfer-Encoding: binary");
            header("Content-Length: ".filesize($realFileInfo)); 
            @readfile($realFileInfo);
            return true;
        }
        return false;
    }
[/PHP]Can anyone suggest what might be the problem? I have been looking at the code and server for about a day now and my head really hurts.

I appreciate any help or suggestions you may have.

---

