---
title: "scanimage crashing"
date: 2013-09-13
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-09-13
Does this only happen to me?
This is what is supposed to happen
```
[COLOR=#00ff00]**chad@M4A79XTD-EVO**[/COLOR]:~$ scanimage -L
device `plustek:libusb:004:002' is a UMAX 3400 flatbed scanner
device `hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5' is a Hewlett-Packard Deskjet_F4400_series all-in-one
chad@M4A79XTD-EVO:~$ scanimage --help -d hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information

Options specific to device `hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5':
  Scan mode:
    --mode Lineart|Gray|Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 75|100|150|200|300|600|1200dpi [75]
        Sets the resolution of the scanned image.
  Advanced:
    --contrast -127..127 [0]
        Controls the contrast of the acquired image.
    --compression None|JPEG [JPEG]
        Selects the scanner compression method for faster scans, possibly at
        the expense of image quality.
    --jpeg-quality 0..100 [10]
        Sets the scanner JPEG compression factor. Larger numbers mean better
        compression, and smaller numbers mean better image quality.
    --batch-scan[=(yes|no)] [no]
        Enables continuous scanning with automatic document feeder (ADF).
    --source Flatbed [Flatbed]
        Selects the scan source (such as a document-feeder).
    --duplex[=(yes|no)] [inactive]
        Enables scanning on both sides of the page.
  Geometry:
    --length-measurement Unknown|Approximate|Padded [Padded]
        Selects how the scanned image length is measured and reported, which
        is impossible to know in advance for scrollfed scans.
    -l 0..215.9mm [0]
        Top-left x position of scan area.
    -t 0..296.926mm [0]
        Top-left y position of scan area.
    -x 0..215.9mm [215.9]
        Width of scan-area.
    -y 0..296.926mm [296.926]
        Height of scan-area.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    plustek:libusb:004:002
    hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5
**[COLOR=#00ff00]chad@M4A79XTD-EVO[/COLOR]**:~$ 
```
What happens for me in saucy
```
[COLOR=#00ff00]**chad@chad-VirtualBox**[/COLOR]:~$ scanimage -L
device `net:10.0.0.50:plustek:libusb:004:002' is a UMAX 3400 flatbed scanner
device `net:10.0.0.50:hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5' is a Hewlett-Packard Deskjet_F4400_series all-in-one
**[COLOR=#00ff00]chad@chad-VirtualBox[/COLOR]**:~$ scanimage -L
device `net:10.0.0.50:plustek:libusb:004:002' is a UMAX 3400 flatbed scanner
device `net:10.0.0.50:hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5' is a Hewlett-Packard Deskjet_F4400_series all-in-one
**[COLOR=#00ff00]chad@chad-VirtualBox[/COLOR]**:~$ scanimage -L
device `net:10.0.0.50:plustek:libusb:004:002' is a UMAX 3400 flatbed scanner
device `net:10.0.0.50:hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5' is a Hewlett-Packard Deskjet_F4400_series all-in-one
[COLOR=#00ff00]**chad@chad-VirtualBox**[/COLOR]:~$ scanimage -L
*** Error in `scanimageSegmentation fault (core dumped)
**[COLOR=#00ff00]chad@chad-VirtualBox[/COLOR]**:~$
```

---

