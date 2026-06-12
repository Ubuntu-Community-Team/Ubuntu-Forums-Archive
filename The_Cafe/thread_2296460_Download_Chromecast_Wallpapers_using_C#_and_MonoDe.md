---
title: "Download Chromecast Wallpapers using C# and MonoDevelop"
date: 2015-09-26
forum: The Cafe
---

### Post by SeanKD on 2015-09-26
I decided to write a small program in C# to download Chromecast Wallpapers. I am providing the code below free for anyone to use. If anyone has any suggestions for improving the code I would love to hear them as I am currently learning C# in university. NOTE: I have tested this on Windows 10 and Ubuntu 14.04 LTS only and it was compiled as a C# Console Application. Your mileage may vary.
```

// Sean K. Davis// Email: sean.k.davis@gmail.com
//
// Chromecast Wallpapers Downloader
//
// This program downloads the current set of Chromecast wallpapers
// and saves them to a directory of your choice
//


using System;
using System.IO;
using System.Net;


namespace ChromecastWallpapers
{
    class ChromecastWallpapers
    {
        static void Main (string[] args)
        {
            using (WebClient client = new WebClient ()) {
                // Set the save directory here
                string directory = "/path/to/save/directory/";


                // Create the directory if it doesn not already exist
                if (!Directory.Exists (directory))
                    Directory.CreateDirectory (directory);


                //Set the working directory
                Directory.SetCurrentDirectory (directory);


                // Set desired size, width, and height
                // I know only that the default(s1280,w1280,h720)
                // and 1080p(s1920,w1920,h1080) work for certain.
                // Other resolutions may be available, but no guarantees
                string picSize = "s1920";
                string picWidth = "w1920";
                string picHeight = "h1080";


                // Download the chromecast screensaver html
                string htmlCode = client.DownloadString ("https://clients3.google.com/cast/chromecast/home");


                // Separator used to split html code
                string[] separators = { "x22" };


                // Split the html code
                string[] lines = htmlCode.Split (separators, StringSplitOptions.RemoveEmptyEntries);


                foreach (string line in lines) {
                    // See if the line contains a URL is for an image file
                    if (line.Contains ("googleusercontent") && line.Contains (".jpg")) {
                        // If so, clean it up so we can use it and
                        // set the desired image resolution for download
                        string fileURL = line.Replace ("\\", "").Replace ("s1280", picSize).Replace ("w1280", picWidth).Replace ("h720", picHeight);


                        //Clean up any html percent codes in the filename
                        //NOTE: You may see others in you downloaded image filenames,
                        //Just append another .Replace("string to replace", "replacement string")
                        //to remove any annoying characters you find in the filenames
                        fileURL = fileURL.Replace ("%2B", " ").Replace ("%25", "");


                        //Let's use this to find the filename
                        //within the file URL
                        separators = new string[] { "/" };


                        string[] fileNames = fileURL.Split (separators, StringSplitOptions.RemoveEmptyEntries);


                        foreach (string fileName in fileNames) {
                            // If we have a valid filename then 
                            // download the file if it doesn't already exist
                            if (fileName.Contains (".jpg") && !File.Exists (fileName)) {
                                //Since this program is running in a terminal,
                                //let the user know which files are being downloaded
                                Console.WriteLine ("Downloading {0}", fileName);


                                //Download the file and save it
                                client.DownloadFile (fileURL, directory + fileName);
                            }                               
                        }
                    }
                }
            }
        }
    }
}

```

---

### Post by Erik1984 on 2015-09-26
Thanks for the script. Maybe a good reason to install Monodevelop. Never tried developing .Net applications on Linux. I'm still learning C# myself but I think that client.Dispose() is not necessary. You declare the client in a **using** block, using takes care of calling Dispose(). [https://msdn.microsoft.com/en-us/library/yh598w02.aspx](https://msdn.microsoft.com/en-us/library/yh598w02.aspx)

---

### Post by SeanKD on 2015-09-27
Thanks for the advice. I'm still trying to get used to the language being garbage collected. I'll adjust the script accordingly.

---

