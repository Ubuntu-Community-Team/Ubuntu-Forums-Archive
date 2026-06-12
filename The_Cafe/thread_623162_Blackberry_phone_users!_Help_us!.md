---
title: "Blackberry phone users! Help us!"
date: 2007-11-25
forum: The Cafe
---

### Post by DoctorMO on 2007-11-25
Hello everyone,

I need people who own a blackberry phone from RIM (Research in Motion) to run the btool program in verbose mode in order to gather as much variable information about attribute information. At the moment we're trying to work out what stuff means from first principles but it's hard to do with out variance.

So first you need to have Barry installed: [http://sourceforge.net/project/showfiles.php?group_id=153722](http://sourceforge.net/project/showfiles.php?group_id=153722)

Once installed please run the following:

sudo rmmod usb_storage; sudo bcharge; sudo btool -v -l &> ~/btool.log; sudo modprobe usb_storage

We have to remove the usb storage module because of a set configuration bug in barry (which is now fixed in cvs). once you have your log file please email it to me at [email]doctormo@gmail.com[/email]

We also need people who use the windows client to use the usb snooper to create windows logs so we can work from those too. email if your interested in helping out.

Regards, Martin (DoctorMO)

---

### Post by prizrak on 2007-11-25
Done, wasn't a 100% sure what to install from the sourceforge site so i grabbed pretty much everything :)

---

### Post by yatt on 2007-11-25
It configures, but it will not compile. It does not like allot of things about data.cc The error:
```
g++ -DHAVE_CONFIG_H -I.. -ansi -Wall -fno-strict-aliasing -g -g -O2 -MT data.lo -MD -MP -MF .deps/data.Tpo -c data.cc  -fPIC -DPIC -o .libs/data.o
data.cc: In constructor 'Barry::Data::Data()':
data.cc:70: error: 'memset' was not declared in this scope
data.cc: In constructor 'Barry::Data::Data(int, size_t)':
data.cc:81: error: 'memset' was not declared in this scope
data.cc: In copy constructor 'Barry::Data::Data(const Barry::Data&)':
data.cc:104: error: 'memcpy' was not declared in this scope
data.cc: In member function 'void Barry::Data::MakeSpace(size_t)':
data.cc:117: error: 'memcpy' was not declared in this scope
data.cc:118: error: 'memset' was not declared in this scope
data.cc: In member function 'void Barry::Data::CopyOnWrite(size_t)':
data.cc:133: error: 'memcpy' was not declared in this scope
data.cc: In member function 'void Barry::Data::Zap()':
data.cc:261: error: 'memset' was not declared in this scope
data.cc: In member function 'Barry::Data& Barry::Data::operator=(const Barry::Data&)':
data.cc:272: error: 'memcpy' was not declared in this scope
data.cc: In function 'bool Barry::IsEndpointStart(const std::string&, int&)':
data.cc:386: error: 'strncmp' was not declared in this scope
data.cc:389: error: 'atoi' was not declared in this scope
make[2]: *** [data.lo] Error 1
make[2]: Leaving directory `/root/barry-0.9/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/barry-0.9'
make: *** [all] Error 2
```

It also warns about casting strings to char*

---

### Post by prizrak on 2007-11-25
> **yatt said:**
> It configures, but it will not compile. It does not like allot of things about data.cc The error:


It also warns about casting strings to char*

Try the debs that's how I installed it. I think all you need is libbarry and barytool.

---

### Post by yatt on 2007-11-25
> **prizrak said:**
> Try the debs that's how I installed it. I think all you need is libbarry and barytool.I'm on an AMD64 machine.

---

### Post by DoctorMO on 2007-11-25
yatt: can you email your results to the barry mailing list? I'm sure Chris would be delighted to hear of AMD64 compile problems :-)

Thanks prizrak

---

### Post by DoctorMO on 2007-11-25
Could someone dig this page? I've got 6 results so far, 1 classic, 2 pearls and 2 curves all of gprs (no cdma yet) could do with more samples.

---

### Post by prizrak on 2007-11-25
I might be able to get you a CDMA sample tomorrow. Some people at work have them.

---

### Post by DoctorMO on 2007-11-26
I know there are more than 2 users of blackberries on these forums. And I know people are generally good to help us with hardware research; so I'm thinking some people have not been able to read this thread through lack of promotion. so *bump*

---

### Post by DrOlaf on 2007-11-26
I've only just got back from a Thanksgiving vacation trip, so this is the first time I've seen the announcement. I have an 8700g on T-Mobile USA GSM/EDGE that I'll run this on later today.

---

### Post by prizrak on 2007-11-26
Couldn't get the CDMA sample :(

---

### Post by DoctorMO on 2007-11-27
Oh well not to worry; if the people emailing me with problems about getting barry to work are anything to go by I'd say we have a lot of work to do just packaging the thing up in a friendly way.

I've got about 8 samples, i really need about 20.

---

### Post by DrOlaf on 2007-11-27
Well, I followed prizrak's advice and got barry installed easily enough from the debs. I've sent in my btool.log.

---

### Post by DoctorMO on 2007-11-27
There is so much variance so far just trying to install it; I think next time I'll prepare a deb with a special script.

Thanks DrOlaf, I've sent you a reply.

---

### Post by DoctorMO on 2007-11-27
OK I've got 12 now, looking better but more are required. come on community power! almost there.

---

### Post by DoctorMO on 2007-12-03
I've managed to get 20, mostly Pearls and Curves although I need more people with Blackberry 7700's, 8800's, 7200's and 6200's to send information, only having 1 of these models is not helping the research. If you have or know of someone that has one of these phones I would be MOST grateful for you to run btool (install version 0.11 of barry we got lots of things fixed to make things easy)

I'll be shocked if out of 100,000 people on ubuntuforums only 3 people have blackberries (that is how many I've gotten from here)

---

### Post by DoctorMO on 2007-12-03
bump

---

### Post by DoctorMO on 2007-12-03
bump

---

### Post by alek01 on 2007-12-04
Hello,
Could you give me some quick instructions please.I have Barry 11 on Gusty and a curve 8320. The BB charges automatically, I can see the media files on BB and exchange files. Can you tell me what to do to SYNC with Evolution? What command? Where to look? Thank you very much.
Alek

---

### Post by DoctorMO on 2007-12-04
alek01, in order to sync you need to install opensync 0.2x and install the barry opensync plugin as well as the evolution opensync plugin. You'll then need to set up a sync configuration from the command line. it isn't pretty.

---

### Post by anothermikemiller on 2007-12-05
I just completed my first compile on Gutsy amd-64.   There are 2 dependacies for Barry: libusb-dev and libssl-dev.  These are both available from synaptics.  The dev for openssl is libssl-dev not openssl-dev or libopenssl-dev.

Running bcharge gave me the following error:
```
$ sudo bcharge
Scanning for Blackberry devices...
Found device #006...adjusting charge setting...adjusting Pearl mode to dualDetecting possible kernel driver conflict, trying to resolve...
usb_reset failed: could not reset: No such device
...done
```

But when I ran doctormo's code it fixed the bcharge error but did not give a log file:
```
$ sudo rmmod usb_storage; sudo bcharge; sudo btool -v -l &> ~/btool.log; sudo modprobe usb_storage
Scanning for Blackberry devices...
Found device #007...already at 500mA...already in desired Pearl mode...no change

```

I don't seem to have access to the sd card yet.

EDIT
I did get the log file.  It outputs to the home directory. This is for the new curve on T-Mobile.  I'll also send my compile information to the mailing list.

---

### Post by prizrak on 2007-12-05
Crap!!! Forgot to bring my laptop to work to try other people's blackberrys :(

---

### Post by DoctorMO on 2007-12-05
Thanks to all your help I've managed to reach a number of conclusions about some of the data. Information is all posted to the barry mailing list for those interested.

There remains some question over the 7200, 7100 and 6200 series phones as these sometimes look like the same series according to the code. If you have one of these phones I would be _VERY_ interested to work with you to get the required debug information.

Thanks again to all those who helped out.

---

### Post by stiperstones on 2007-12-06
Hi quick reply to your post



```

btool: error while loading shared libraries: libboost_serialization.so.1.33.1: cannot open shared object file: No such file or directory

output mesage from command line
$ sudo rmmod usb_storage; sudo bcharge; sudo btool -v -l &> ~/btool.log; sudo modprobe usb_storage
Scanning for Blackberry devices...
Found device #005...already at 500mA...no Pearl adjustment...no change


Phone Blackberry 7130g

```

---

### Post by PartisanEntity on 2007-12-06
My mother has a BB, at the next possible opportunity I shall send you the info.

(Silly question, but do I run the script on my laptop while the BB is connected to it or how does this tool work?)

---

### Post by stiperstones on 2007-12-06
connect the phone and run the command in a terminal look at first post and install needed software

```

sudo rmmod usb_storage; sudo bcharge; sudo btool -v -l &> ~/btool.log; sudo modprobe usb_storage

```

then copy the output here also give the type of phone please

---

### Post by stiperstones on 2007-12-06
Output of usb snoop from winXP for blackberry 7130g may help someone

```

[0 ms] UsbSnoop compiled on Jan 18 2003 22:41:32 loading
[0 ms] UsbSnoop - DriverEntry(babd9c40) : Windows NT WDM version 1.32
[5 ms] UsbSnoop - AddDevice(babd9f50) : DriverObject 86461d30, pdo 85c3a398
[5 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_PNP (0x00000018)
[5 ms] UsbSnoop - MyDispatchPNP(babd9ee0) : IRP_MJ_PNP (0x00000018)
[8 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_PNP (IRP_MN_QUERY_RESOURCE_REQUIREMENTS)
[8 ms] UsbSnoop - MyDispatchPNP(babd9ee0) : IRP_MJ_PNP (IRP_MN_QUERY_RESOURCE_REQUIREMENTS)
[8 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_PNP (IRP_MN_FILTER_RESOURCE_REQUIREMENTS)
[8 ms] UsbSnoop - MyDispatchPNP(babd9ee0) : IRP_MJ_PNP (IRP_MN_FILTER_RESOURCE_REQUIREMENTS)
[8 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_PNP (IRP_MN_START_DEVICE)
[8 ms] UsbSnoop - MyDispatchPNP(babd9ee0) : IRP_MJ_PNP (IRP_MN_START_DEVICE)
[9 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_INTERNAL_DEVICE_CONTROL
[9 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_SYSTEM_CONTROL
[9 ms] UsbSnoop - MyDispatchInternalIOCTL(babd8e80) : fdo=85c3a398, Irp=85c38998, IRQL=0
[9 ms]  >>>  URB 1 going down  >>> 
-- URB_FUNCTION_GET_DESCRIPTOR_FROM_DEVICE:
  TransferBufferLength = 00000012
  TransferBuffer       = 8641dc80
  TransferBufferMDL    = 00000000
  Index                = 00000000
  DescriptorType       = 00000001 (USB_DEVICE_DESCRIPTOR_TYPE)
  LanguageId           = 00000000
[10 ms] UsbSnoop - MyInternalIOCTLCompletion(babd8db0) : fido=00000000, Irp=85c38998, Context=864509e0, IRQL=2
[10 ms]  <<<  URB 1 coming back  <<< 
-- URB_FUNCTION_CONTROL_TRANSFER:
  PipeHandle           = 85d9b768
  TransferFlags        = 0000000b (USBD_TRANSFER_DIRECTION_IN, USBD_SHORT_TRANSFER_OK)
  TransferBufferLength = 00000012
  TransferBuffer       = 8641dc80
  TransferBufferMDL    = 86696568
    00000000: 12 01 10 01 ff ff ff 10 ca 0f 01 00 04 01 01 02
    00000010: 00 01
  UrbLink              = 00000000
  SetupPacket          =
    00000000: 80 06 00 01 00 00 12 00
[10 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_INTERNAL_DEVICE_CONTROL
[10 ms] UsbSnoop - MyDispatchInternalIOCTL(babd8e80) : fdo=85c3a398, Irp=85c38998, IRQL=0
[10 ms]  >>>  URB 2 going down  >>> 
-- URB_FUNCTION_GET_DESCRIPTOR_FROM_DEVICE:
  TransferBufferLength = 00000009
  TransferBuffer       = 8634dde8
  TransferBufferMDL    = 00000000
  Index                = 00000001
  DescriptorType       = 00000002 (USB_CONFIGURATION_DESCRIPTOR_TYPE)
  LanguageId           = 00000000
[11 ms] UsbSnoop - MyInternalIOCTLCompletion(babd8db0) : fido=00000000, Irp=85c38998, Context=86490310, IRQL=2
[11 ms]  <<<  URB 2 coming back  <<< 
-- URB_FUNCTION_CONTROL_TRANSFER:
  PipeHandle           = 85d9b768
  TransferFlags        = 0000000b (USBD_TRANSFER_DIRECTION_IN, USBD_SHORT_TRANSFER_OK)
  TransferBufferLength = 00000009
  TransferBuffer       = 8634dde8
  TransferBufferMDL    = 86696568
    00000000: 09 02 2e 00 01 01 00 80 fa
  UrbLink              = 00000000
  SetupPacket          =
    00000000: 80 06 01 02 00 00 09 00
[11 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_INTERNAL_DEVICE_CONTROL
[11 ms] UsbSnoop - MyDispatchInternalIOCTL(babd8e80) : fdo=85c3a398, Irp=85c38998, IRQL=0
[11 ms]  >>>  URB 3 going down  >>> 
-- URB_FUNCTION_GET_DESCRIPTOR_FROM_DEVICE:
  TransferBufferLength = 0000002e
  TransferBuffer       = 85885b10
  TransferBufferMDL    = 00000000
  Index                = 00000001
  DescriptorType       = 00000002 (USB_CONFIGURATION_DESCRIPTOR_TYPE)
  LanguageId           = 00000000
[12 ms] UsbSnoop - MyInternalIOCTLCompletion(babd8db0) : fido=00000000, Irp=85c38998, Context=86504bf8, IRQL=2
[12 ms]  <<<  URB 3 coming back  <<< 
-- URB_FUNCTION_CONTROL_TRANSFER:
  PipeHandle           = 85d9b768
  TransferFlags        = 0000000b (USBD_TRANSFER_DIRECTION_IN, USBD_SHORT_TRANSFER_OK)
  TransferBufferLength = 0000002e
  TransferBuffer       = 85885b10
  TransferBufferMDL    = 86696568
    00000000: 09 02 2e 00 01 01 00 80 fa 09 04 00 00 04 ff ff
    00000010: ff 00 07 05 81 02 40 00 00 07 05 02 02 40 00 00
    00000020: 07 05 83 02 40 00 00 07 05 04 02 40 00 00
  UrbLink              = 00000000
  SetupPacket          =
    00000000: 80 06 01 02 00 00 2e 00
[12 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_INTERNAL_DEVICE_CONTROL
[12 ms] UsbSnoop - MyDispatchInternalIOCTL(babd8e80) : fdo=85c3a398, Irp=85c38998, IRQL=0
[13 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_INTERNAL_DEVICE_CONTROL
[13 ms] UsbSnoop - MyDispatchInternalIOCTL(babd8e80) : fdo=85c3a398, Irp=85c38998, IRQL=0
[13 ms]  >>>  URB 4 going down  >>> 
-- URB_FUNCTION_SELECT_CONFIGURATION:
  ConfigurationDescriptor = 0x85885b10 (configure)
  ConfigurationDescriptor : bLength             = 9
  ConfigurationDescriptor : bDescriptorType     = 0x00000002
  ConfigurationDescriptor : wTotalLength        = 0x0000002e
  ConfigurationDescriptor : bNumInterfaces      = 0x00000001
  ConfigurationDescriptor : bConfigurationValue = 0x00000001
  ConfigurationDescriptor : iConfiguration      = 0x00000000
  ConfigurationDescriptor : bmAttributes        = 0x00000080
  ConfigurationDescriptor : MaxPower            = 0x000000fa
  ConfigurationHandle     = 0x00000000
  Interface[0]: Length            = 96
  Interface[0]: InterfaceNumber   = 0
  Interface[0]: AlternateSetting  = 0
[84 ms] UsbSnoop - MyInternalIOCTLCompletion(babd8db0) : fido=00000000, Irp=85c38998, Context=8657c728, IRQL=0
[84 ms]  <<<  URB 4 coming back  <<< 
-- URB_FUNCTION_SELECT_CONFIGURATION:
  ConfigurationDescriptor = 0x85885b10 (configure)
  ConfigurationDescriptor : bLength             = 9
  ConfigurationDescriptor : bDescriptorType     = 0x00000002
  ConfigurationDescriptor : wTotalLength        = 0x0000002e
  ConfigurationDescriptor : bNumInterfaces      = 0x00000001
  ConfigurationDescriptor : bConfigurationValue = 0x00000001
  ConfigurationDescriptor : iConfiguration      = 0x00000000
  ConfigurationDescriptor : bmAttributes        = 0x00000080
  ConfigurationDescriptor : MaxPower            = 0x000000fa
  ConfigurationHandle     = 0x858b0320
  Interface[0]: Length            = 96
  Interface[0]: InterfaceNumber   = 0
  Interface[0]: AlternateSetting  = 0
  Interface[0]: Class             = 0x000000ff
  Interface[0]: SubClass          = 0x000000ff
  Interface[0]: Protocol          = 0x000000ff
  Interface[0]: InterfaceHandle   = 0x864d4008
  Interface[0]: NumberOfPipes     = 4
  Interface[0]: Pipes[0] : MaximumPacketSize = 0x00000040
  Interface[0]: Pipes[0] : EndpointAddress   = 0x00000081
  Interface[0]: Pipes[0] : Interval          = 0x00000000
  Interface[0]: Pipes[0] : PipeType          = 0x00000002 (UsbdPipeTypeBulk)
  Interface[0]: Pipes[0] : PipeHandle        = 0x864d4024
  Interface[0]: Pipes[0] : MaxTransferSize   = 0x00004000
  Interface[0]: Pipes[0] : PipeFlags         = 0x00000000
  Interface[0]: Pipes[1] : MaximumPacketSize = 0x00000040
  Interface[0]: Pipes[1] : EndpointAddress   = 0x00000002
  Interface[0]: Pipes[1] : Interval          = 0x00000000
  Interface[0]: Pipes[1] : PipeType          = 0x00000002 (UsbdPipeTypeBulk)
  Interface[0]: Pipes[1] : PipeHandle        = 0x864d4044
  Interface[0]: Pipes[1] : MaxTransferSize   = 0x00004000
  Interface[0]: Pipes[1] : PipeFlags         = 0x00000000
  Interface[0]: Pipes[2] : MaximumPacketSize = 0x00000040
  Interface[0]: Pipes[2] : EndpointAddress   = 0x00000083
  Interface[0]: Pipes[2] : Interval          = 0x00000000
  Interface[0]: Pipes[2] : PipeType          = 0x00000002 (UsbdPipeTypeBulk)
  Interface[0]: Pipes[2] : PipeHandle        = 0x864d4064
  Interface[0]: Pipes[2] : MaxTransferSize   = 0x00004000
  Interface[0]: Pipes[2] : PipeFlags         = 0x00000000
  Interface[0]: Pipes[3] : MaximumPacketSize = 0x00000040
  Interface[0]: Pipes[3] : EndpointAddress   = 0x00000004
  Interface[0]: Pipes[3] : Interval          = 0x00000000
  Interface[0]: Pipes[3] : PipeType          = 0x00000002 (UsbdPipeTypeBulk)
  Interface[0]: Pipes[3] : PipeHandle        = 0x864d4084
  Interface[0]: Pipes[3] : MaxTransferSize   = 0x00004000
  Interface[0]: Pipes[3] : PipeFlags         = 0x00000000
[84 ms] UsbSnoop - IRP_MJ_POWER (IRP_MN_SET_POWER), SystemContext 00000003[84 ms] , DevicePowerState = PowerDeviceUnspecified
[85 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_PNP (IRP_MN_QUERY_CAPABILITIES)
[85 ms] UsbSnoop - MyDispatchPNP(babd9ee0) : IRP_MJ_PNP (IRP_MN_QUERY_CAPABILITIES)
[86 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_PNP (IRP_MN_QUERY_PNP_DEVICE_STATE)
[86 ms] UsbSnoop - MyDispatchPNP(babd9ee0) : IRP_MJ_PNP (IRP_MN_QUERY_PNP_DEVICE_STATE)
[86 ms] UsbSnoop - DispatchAny(babd7610) : IRP_MJ_PNP (IRP_MN_QUERY_DEVICE_RELATIONS)
[86 ms] UsbSnoop - MyDispatchPNP(babd9ee0) : IRP_MJ_PNP (IRP_MN_QUERY_DEVICE_RELATIONS)

```

---

### Post by DoctorMO on 2007-12-06
stiperstones: have you tried to install the missing library? I better let Chris know there is a dependency problem too. Thanks for your help so far, windows logs are always useful too.

---

### Post by stiperstones on 2007-12-06
not yet cannot find source libboost_serialization yet i could use a rpm file and alien  would be better than nothing

---

### Post by DoctorMO on 2007-12-06
I believe the package may be called boost

---

### Post by stiperstones on 2007-12-06
hi DoctorMO
Here's my problem

current btool source package requires library  libboost_serialization.so.1.33.1

installed library  libboost-serialization1.34.1

---

### Post by DoctorMO on 2007-12-06
Sounds like Chris built the deb on debian etch; you can compile it quite easily by installing build-essential, libusb-dev and libssl-dev

---

### Post by BDNiner on 2007-12-06
I came upon this post today. I have a 8703e but i cannot get the software working. I installed the debs from the website but for some reason i don't have bcharge installed. When i tried to compile the code i was missing libusb and openssl.

Where can i find libusb?? i have the latest version of openssl.

---

### Post by DoctorMO on 2007-12-06
> Where can i find libusb?? i have the latest version of openssl.

sudo apt-get install libusb-dev libssl-dev build-essential

The deb packages obviously have some problems :-/

---

### Post by stiperstones on 2007-12-06
I tried installing the deb files from the barry site but encountered some problems so  i rebuilt the suse10 rpms using alien and installed those

---

### Post by BDNiner on 2007-12-06
When i run your command from the first post i get this error:

ERROR: Module usb_storage does not exist in /proc/modules

If i can get this working i can really help you since we have a lot of blackberries here at work.

After a restart it created the log file. I will e-mail the file to you. Let me know if you still need log files from other blackberries.

---

### Post by DoctorMO on 2007-12-06
> If i can get this working i can really help you since we have a lot of blackberries here at work.

OK that error isn't important, that should mean that your run was successful and you should pass me the log file.

The error indicates that your computer doesn't have the usb_storage kernel module installed.

---

### Post by BDNiner on 2007-12-06
It seems like everytime i connect a new blackberry I have to restart for the log file to be created properly. Do you want me to send the log file i recieve before i restart or tell me what i need to do in order to create another log file.

I have e-mailed you 2 log for a 7130e and 8703e.

---

### Post by DoctorMO on 2007-12-06
Yes it would be VERY useful to see such errors, can you email them to the mailing list or email them to me and I'll put them in the bug tracker.

Thanks so much for those, they are exactly the models I'm missing.

---

### Post by stiperstones on 2007-12-06
reinstalled barry 11 from source file bz2 here is the output from btool
```

usb_set_debug: Setting debugging level to 9 (on)
usb_os_init: Found USB VFS at /dev/bus/usb
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 002 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 003 on 002
usb_os_find_devices: Found 002 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 004 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
device_desc loaded
bLength: 18
bDescriptorType: 1
bcdUSB: 272
bDeviceClass: 255
bDeviceSubClass: 255
bDeviceProtocol: 255
bMaxPacketSize0: 16
idVendor: 4042
idProduct: 1
bcdDevice: 260
iManufacturer: 1
iProduct: 2
iSerialNumber: 0
bNumConfigurations: 1

  config_desc #0 loaded
bLength: 9
bDescriptorType: 2
wTotalLength: 46
bNumInterfaces: 1
bConfigurationValue: 1
iConfiguration: 0
bmAttributes: 128
MaxPower: 50

    interface_desc #0 loaded
bLength: 9
bDescriptorType: 4
bInterfaceNumber: 0
bAlternateSetting: 0
bNumEndpoints: 4
bInterfaceClass: 255
bInterfaceSubClass: 255
bInterfaceProtocol: 255
iInterface: 0

      endpoint_desc #0 loaded
bLength: 7
bDescriptorType: 5
bEndpointAddress: 129
bmAttributes: 2
wMaxPacketSize: 64
bInterval: 0
bRefresh: 0
bSynchAddress: 0

      endpoint added to map with bEndpointAddress: 129
        pair.read = 129
        pair.type = 2
      endpoint_desc #1 loaded
bLength: 7
bDescriptorType: 5
bEndpointAddress: 2
bmAttributes: 2
wMaxPacketSize: 64
bInterval: 0
bRefresh: 0
bSynchAddress: 0

      endpoint added to map with bEndpointAddress: 2
        pair.write = 2
        pair.type = 2
        pair added! (read: 129,write: 2,type: 2)
      endpoint_desc #2 loaded
bLength: 7
bDescriptorType: 5
bEndpointAddress: 131
bmAttributes: 2
wMaxPacketSize: 64
bInterval: 0
bRefresh: 0
bSynchAddress: 0

      endpoint added to map with bEndpointAddress: 131
        pair.read = 131
        pair.type = 2
      endpoint_desc #3 loaded
bLength: 7
bDescriptorType: 5
bEndpointAddress: 4
bmAttributes: 2
wMaxPacketSize: 64
bInterval: 0
bRefresh: 0
bSynchAddress: 0

      endpoint added to map with bEndpointAddress: 4
        pair.write = 4
        pair.type = 2
        pair added! (read: 131,write: 4,type: 2)
    interface added to map with bInterfaceNumber: 0
  config added to map with bConfigurationValue: 1
usb_open(0x8095900)
usb_claim_interface(0x808cc60,0)
usb_clear_halt(0x808cc60,131)
usb_clear_halt(0x808cc60,4)
BulkWrite to endpoint 4:
    00000000: 00 00 10 00 01 ff 00 00 a8 18 da 8d 6c 02 00 00  ............l...

BulkRead (131):
    00000000: 00 00 10 00 02 ff 00 00 a8 18 da 8d 6c 02 00 00  ............l...

BulkWrite to endpoint 4:
    00000000: 00 00 0c 00 05 ff 00 00 14 00 01 00              ............

Socket::Send: Endpoint 131
Received:
    00000000: 00 00 20 00 06 ff 00 00 14 00 01 00 3d 89 b5 9c  .. .........=...
    00000010: 0c 5d 99 89 fc 10 a7 49 09 1d 6e 0a 70 a6 b3 10  .].....I..n.p...

BulkWrite to endpoint 4:
    00000000: 00 00 0c 00 05 ff 00 01 08 00 04 00              ............

Socket::Send: Endpoint 131
Received:
    00000000: 00 00 14 00 06 ff 00 01 08 00 04 00 03 00 00 00  ................
    00000010: 0f 45 fe 24                                      .E.$

BulkWrite to endpoint 4:
    00000000: 00 00 0c 00 05 ff 00 02 08 00 02 00              ............

Socket::Send: Endpoint 131
Received:
    00000000: 00 00 c4 01 06 ff 00 02 b8 01 02 00 09 00 04 00  ................
    00000010: b8 01 00 00 01 13 02 05 03 09 00 84 52 49 4d 20  ............RIM 
    00000020: 37 31 30 30 20 53 65 72 69 65 73 20 43 6f 6c 6f  7100 Series Colo
    00000030: 75 72 20 47 50 52 53 20 48 61 6e 64 68 65 6c 64  ur GPRS Handheld
    00000040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
    00000050: 00 00 00 00 00 00 00 00 00 00 00 00 6e 70 61 72  ............npar
    00000060: 74 68 69 62 61 6e 00 00 00 00 00 00 4d 61 79 20  thiban......May 
    00000070: 30 33 20 32 30 30 36 00 00 00 00 00 31 30 3a 33  03 2006.....10:3
    00000080: 37 3a 35 31 00 00 00 00 00 00 00 00 00 01 0f 00  7:51............
    00000090: 00 00 00 00 00 00 00 00 a4 00 00 00 0a 00 00 00  ................
    000000a0: b8 00 00 00 40 00 00 00 02 00 00 00 e8 5f 00 80  ....@........_..
    000000b0: 01 08 02 c5 03 02 04 0e 07 11 ff ff ff ff ff ff  ................
    000000c0: ff ff ff ff 4a 56 be 92 0b 00 01 00 03 0c 00 00  ....JV..........
    000000d0: 00 00 00 80 ff ff 3f 80 03 0c 00 01 00 00 00 84  ......?.........
    000000e0: ff ff 07 84 03 0c 01 00 00 00 00 04 ff ff ff 05  ................
    000000f0: 03 0c 01 01 00 00 00 08 ff ff ff 09 01 0c 00 00  ................
    00000100: 00 00 02 80 ff ff 35 80 07 14 00 00 00 00 02 00  ......5.........
    00000110: 00 00 02 04 ff ff fd 05 00 00 02 00 07 14 00 00  ................
    00000120: 00 00 02 00 00 00 02 08 ff ff ff 09 00 00 02 00  ................
    00000130: 05 14 00 00 00 00 01 00 00 00 36 80 ff ff 39 80  ..........6...9.
    00000140: 00 00 01 00 0c 0c 00 00 00 00 3a 80 ff ff 3b 80  ..........:...;.
    00000150: 0e 10 00 00 00 00 3c 80 ff ff 3f 80 00 00 01 00  ......<...?.....
    00000160: 12 0c 00 00 00 00 00 84 ff ff 07 84 09 08 00 00  ................
    00000170: fe 34 a2 e0 ff ff ff ff ff ff ff ff ff ff ff ff  .4..............
    00000180: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
    00000190: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
    000001a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
    000001b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
    000001c0: ff ff ff ff                                      ....

BulkWrite to endpoint 4:
    00000000: 00 00 0c 00 05 ff 00 03 04 00 05 00              ............

Socket::Send: Endpoint 131
Received:
    00000000: 00 00 0c 00 06 ff 00 03 00 00 00 00              ............

BulkWrite to endpoint 4:
    00000000: 00 00 0c 00 05 ff 00 04 04 00 06 00              ............

Socket::Send: Endpoint 131
Received:
    00000000: 00 00 10 00 06 ff 00 04 04 00 06 00 00 01 00 00  ................

BulkWrite to endpoint 4:
    00000000: 00 00 0c 00 05 ff 00 05 04 00 07 00              ............

Socket::Send: Endpoint 131
Received:
    00000000: 00 00 10 00 06 ff 00 05 04 00 07 00 00 02 00 00  ................

BulkWrite to endpoint 4:
    00000000: 00 00 0c 00 05 ff 00 06 04 00 08 00              ............

Socket::Send: Endpoint 131
Received:
    00000000: 00 00 0c 00 06 ff 00 06 00 00 00 00              ............

Using ReadEndpoint: 131
      WriteEndpoint: 4
usb_release_interface(0x808cc60,0)
usb_close(0x808cc60)
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 002 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 003 on 002
usb_os_find_devices: Found 002 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 004 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
Blackberry devices found:
Device ID: 0x8095900. PIN: 24fe450f, Description: RIM 7100 Series Colour GPRS Handheld
```

---

### Post by BDNiner on 2007-12-06
The head of Blackberry/ Exchange department in my office wanted to send the infomation for the Blackberry 8830 World phone. But the log file generated is just like the last one that i e-mailed you. Even after a restart the log file is no good. But my linux box detects the phone, even the mem stick is mounted to the desktop. But it won't charge, the blackberry displays a message on its screen that there is not enough USB power coming to the phone to charge it, please try a different USB port. The owner of the phone said that it will not charge in fedora or ubuntu but charges fine on his vista and mac.

---

### Post by DoctorMO on 2007-12-06
You have to run bcharge first, if bcharge is not changing the status properly then make sure berry_charge module is in your modules blacklist and that your running the very latest version of barry (chris fixed some issues with 8800 series recently)

Thanks car, perfect data.

---

### Post by BDNiner on 2007-12-06
> **DoctorMO said:**
> You have to run bcharge first, if bcharge is not changing the status properly then make sure berry_charge module is in your modules blacklist and that your running the very latest version of barry (chris fixed some issues with 8800 series recently)

Thanks car, perfect data.

bcharge detects that the phone is there. How do i make sure berry_charge module is in my modules blacklist?

---

### Post by DoctorMO on 2007-12-06
sudo echo "blacklist usb_storage" >> /etc/modprobe.d/blacklist

You also need to make sure that the phone is going into the right mode, run lsusb and post the results here.

---

### Post by BDNiner on 2007-12-06
When i run lsusb it lists a RIM device on BUS 2, Device 6. when i run 
"sudo echo "blacklist usb_storage" >> /etc/modprobe.d/blacklist" 
i get a permission denied error even though i am using sudo.

---

### Post by DoctorMO on 2007-12-07
edit the blacklist file with your favourite editor under sudo and add the blacklist rule.

---

### Post by samtrevino on 2008-01-06
> **DoctorMO said:**
> alek01, in order to sync you need to install opensync 0.2x and install the barry opensync plugin as well as the evolution opensync plugin. You'll then need to set up a sync configuration from the command line. it isn't pretty.

I have this same issue. It would appear that you may have a solution. If not then please at least tell me how to get the evo2-sync plugin? 

My issue is as follows:

sam@sam-laptop:~$ msynctool --addmember Blackberry evo2-sync
Unable to instance plugin with name evo2-sync: Unable to find the plugin "evo2-sync"

As far as I know I have installed all required opensync 0.2x files, plugins etc. This evo2-sync is the only thing killing me. I have conducted research on the web for over a two days and have found NOTHING regarding specifics about this plugin, which is highly unusual. I have found plenty of vague references saying I will need to install the plugin, but no specifics on how to or where the plugin is located. Any help would be strongly appreciated. 

Also you are requesting logs, but assuming that I know where this log exists, how to produce or obtain said log. Please post clearer instructions (terminal or folder paths) so I may provide this data to you. Please, understand that I am new to Linux and what may be simple to you is not so to me. However, I am willing to provide any information to developers to further research for Blackberry devices. 

Thanks,

Sam

---

### Post by DoctorMO on 2008-01-06
> My issue is as follows:

sam@sam-laptop:~$ msynctool --addmember Blackberry evo2-sync
Unable to instance plugin with name evo2-sync: Unable to find the plugin "evo2-sync"

You will have to forgive my obscure nature, I'm a programmer trying to dig this functionality out of the stone age so I know far more in depth then anyone really ever should.

The msynctool tool allows you to list the plugins that have been installed, it's important to note how you installed the plugins and opensync library since installing from source puts the plugins in one place and installing from deb puts them in a second place.

msynctool --help

There are no logs at this time that I require. I wish you good luck, although if you are as new to linux as you say it might be worth waiting until my project to clean up the functionality is finished. The hope is that simply plugging in a new phone will allow you to sync it by then.

---

### Post by piercleo on 2008-01-08
Hello all, I post on this thread because it seems that you guys will know the answer to my question, sorry if it is an improper place to do so.

I am trying to install barry on my machine but can't find the proper packages. I am running Gutsy 64bits.

I downloaded the rpm file (barry-0.11-1.fc7.src.rpm) on source fourge but got an error regarding the architecture being 64bits when I used Alien to convert it.

I am a newbie to Ubuntu and not really a computer Geek. I run Ubuntu for 6 months now and am very happy with it, except I got a Blackberry and would like to sync it with evolution contacts and calendar. I would love not having to go back to Windows just for this but I can't do without synchronising my phone with my computer.

Best regards,

PC

---

### Post by DoctorMO on 2008-01-08
Well firstly you shouldn't use rpm's when the sources are available, it's better and cleaner to install from source. Although in this case there are deb files you can download and install too.

There are known issues with 64bit when you finally get it installed, so if you have any problems do post a bug report.

---

### Post by piercleo on 2008-01-08
I've been looking for the deb files but couldn't find them. Could someone post a link. No problem wih the bug report though I would prefer not to encounter any problem :-)

---

### Post by DoctorMO on 2008-01-08
[http://sourceforge.net/project/showfiles.php?group_id=153722](http://sourceforge.net/project/showfiles.php?group_id=153722)

The list of debs is for i386 so you may want to install from the source .tar.bz2

---

### Post by piercleo on 2008-01-08
Thanks but i'm having problems with the installation. I'll create a new thread not to polute this one.

---

### Post by piercleo on 2008-01-08
Hey DoctorMO, if you have the time, could you take a look at my problem:

[http://ubuntuforums.org/showthread.php?t=661785](http://ubuntuforums.org/showthread.php?t=661785)

Thank you, 
PC

---

### Post by sangamc on 2008-01-20
i have a bb8830 world phone. i installed barry, and sent you the output file. i just wanted to see what kind of progress you have made with this project. (and bump the post)

---

### Post by DoctorMO on 2008-01-20
Well the developers of the Blackberry software have disappeared of the face of the earth on the mailing list; the open sync guys continue to be blind to real users needs and the conduit programmers still think an extension will be good enough to deal with all hardware syncing to opensync.

It's rather a mess.

---

### Post by sangamc on 2008-01-20
what about vzaccess mgr or the tether feature. i would love to be able to use those tools

---

### Post by toupeiro on 2008-02-01
*Steps up and raises hand*

Work just upgraded my phone to a blackberry 8830 world edition, and I've had the majority of this evening to mess around with it.

I'll snag barry and do what I can to help, but I will also share a bit of what I have learned.

I use a BES for work, so syncing emails and contacts for me is not a huge deal, but I have been successful on syncing files/videos/ringtones etc via bluetooth on both Windows and Linux save a few roadblocks.  First, I will go over Windows because .. afterall..  It SHOULD be easiest on the devices natively supported OS (although I am about to prove otherwise)

1:) Windows:
First off, RIM should be shot!  There is only a small handful of bluetooth adapters that their own software communicate with.  And.. you guessed it, mine wasn't one of them (A 100m belkin BT2.0 USB adapter).  So, here is the skinny on whats going on.  The Blackberry desktop manager software is designed only to communicate with the Microsoft Bluetooth stack, and furthermore, will only work with WHQL certified devices.  Now, for those of you who have a bluetooth adapter, attached is a list of WHQL certified adapters that will work with the microsoft stack AND with RIM's software:

> 
ALPS Integrated Bluetooth DeviceUSB\Vid_044e&Pid_3005
Alps Bluetooth USB AdapterUSB\Vid_044e&Pid_3006
Belkin Bluetooth AdapterUSB\Vid_050d&Pid_0081
Belkin Bluetooth AdapterUSB\Vid_050d&Pid_0084
Blutonium BCM2035
Bluetooth 2.4 GHz Single Chip TransceiverUSB\VID_0A5C&PID_200A
Brain Boxes USB Bluetooth Adapter BL-554USB\Vid_05d1&Pid_0003
BCM2033 Bluetooth 2.4 GHz Single Chip TransceiverUSB\VID_0A5C&PID_200F Generic Bluetooth RadioUSB\Vid_0a12&Pid_0001
CSR NanosiraUSB\Vid_0a12&Pid_0003
CSR Nanosira WHQL Reference RadioUSB\Vid_0a12&Pid_0004
CSR Nanosira-MultimediaUSB\Vid_0a12&Pid_0005
CSR Nanosira-Multimedia WHQL Reference RadioUSB\Vid_0a12&Pid_0006
Dell TrueMobile Bluetooth ModuleUSB\VID_413C&PID_8000
FIC Bluetooth Wireless AdapterUSB\Vid_05b1&Pid_1389
GVC Bluetooth Wireless AdapterUSB\Vid_0525&Pid_a220
IBM Integrated Bluetooth IIUSB\Vid_1668&Pid_0441
Microsoft Wireless Transceiver for BluetoothUSB\Vid_045e&Pid_007e
Silicon Wave Bluetooth Wireless AdapterUSB\Vid_0c10&Pid_0000&Rev_1350
Silicon Wave Bluetooth Wireless AdapterUSB\Vid_0c10&Pid_0000
USB Bluetooth DeviceUSB\Vid_044E&Pid_3002
USB Bluetooth DeviceUSB\Vid_044E&Pid_3003
Sony Bluetooth USB AdapterUSB\Vid_044E&Pid_3004
TDK Bluetooth USB AdapterUSB\Vid_04BF&Pid_0319
TDK Bluetooth USB AdaptorUSB\VID_04BF&PID_0320
TOSHIBA Integrated BluetoothUSB\Vid_0930&Pid_0502&Rev_1350
TOSHIBA Integrated Bluetooth 2USB\Vid_0930&Pid_0505
Dell Wireless 350 Bluetooth ModuleUSB\VID_413C&PID_8103
Bluetooth USB Adapter (BT-51x serial)USB\Vid_0b7a&Pid_07d0&Rev_0126
Bluetooth USB Adapter (BT-51x serial)USB\Vid_0b7a&Pid_07d0&Rev_0133
"HP USB BT Transceiver [1.2]"USB\Vid_03F0&Pid_0C24
IBM Integrated Bluetooth IIIUSB\Vid_1668&Pid_2441
Microsoft Wireless Transceiver for Bluetooth 2.0USB\Vid_045e&Pid_009c
Motion Computing USB Bluetooth DeviceUSB\Vid_10ab&Pid_1002
USB Bluetooth Wireless AdapterUSB\Vid_1310&Pid_0001
USB Bluetooth DeviceUSB\Vid_044E&Pid_3007
TDK Bluetooth USB AdapterUSB\Vid_04BF&Pid_0319
TDK Bluetooth USB AdapterUSB\VID_04BF&PID_0320
TOSHIBA Integrated Bluetooth 3USB\VID_0930&PID_0506
TOSHIBA Bluetooth AdapterUSB\Vid_0930&Pid_0507
Zeevo Bluetooth SolutionUSB\Vid_0b7a&Pid_07d0&Rev_0126
Zeevo Bluetooth SolutionUSB\Vid_0b7a&Pid_07d0&Rev_0133



Now, before you run out to the store with this as a shopping list, I have some news for you.  The only way to get the Vid and Pid of the devices is to plug them in!  As you can see, Belkin BT devices are listed, but my Vid and Pid revisions are higher than the ones officially supported.  To find out what your Vid and Pid are, the device must be installed, and you can see it in the windows device manager by right-clicking on the adapter, going to properties, and going under options. Sure, your device may be working in windows without all this, but not fully functional enough for BDM to see it. But, there is hope so don't throw away or return your USB BT device just yet!  You can trick windows into thinking it is a WHQL supported device.  To do this, you have to edit the file  %windir%\inf\bth.inf with notepad.  (Make sure any bluetooth software or devices are removed first so it works cleanly.)

> Start | run | notepad %windir%\inf\bth.inf

In this file, you will see a Device Section Start, and I just added my info on one of the sections: (remove the &Rev section if you have one for your device, its not needed here)

;----------------------- Device section - Start -----------------------

[ALPS.NT.5.1]
ALPS Integrated Bluetooth Device= BthUsb, USB\Vid_044e&Pid_3005
Alps Bluetooth USB Adapter= BthUsb, USB\Vid_044e&Pid_3006

[Belkin.NT.5.1]
Belkin Bluetooth Adapter= BthUsb, USB\Vid_050d&Pid_0081
Belkin Bluetooth Adapter= BthUsb, USB\Vid_050d&Pid_0084
My flippin USB adapterr = BthUsb, USB\Vid_050d&Pid_0104   <---- Me

Now, I save the file and insert my USB BT device and let windows detect it and install the necessary software.  The beautiful thing here is, it will actually name the device "My flippin USB adapterr" if thats the label you give it. (So have some fun, you deserve it.)

This will give you what should be 'out of the box' bluetooth functionality in Windows.


Now for linux.

The usb device was easy.  I just had to add the following enty to /etc/modprobe.d/blacklist
> 
# added for Bluetooth adapter from belkin
blacklist pegasus

 and reboot.  The device was automatically detected by Ubuntu 7.10 64-bit on reboot.  

Next, I installed a few utilities:
> sudo apt-get install gnome-bluetooth bluez-utils

Once this is done, I right-click on my bluetooth icon in the upper menu bar and click browse device.  If my BB is setup to be discovered, you can get paired in connected in seconds.

From here, all that needs to be done is to put the BB in receive file mode, then right click /send-to on a file in nautilus and choose your blackberry 8830.

alternatively, you can use gnome-obex-send -mtu=65536 <filename.mp3> from the CLI should you choose to. 


The procedure was 10 fold easier to accomplish in linux than in windows, but for reasons of speed, I too want to be able to use my USB cable to access my BB in mass storage mode and use the broadband modem features (and usb charging)

I hope this helps some of you get a few things accomplished on your 8830's, now lets get USB syncing and charging to work!

---

### Post by Griff on 2008-02-18
Works great!  I'm emailing the btool debugging info now! :)

---

### Post by bigmack83 on 2008-03-20
I have connected my Sprint Blackberry 7130e by tethering it to my ubuntu laptop (7.1 Gutsy). Here is my post

[http://ubuntuforums.org/showthread.php?p=4550979#post4550979](http://ubuntuforums.org/showthread.php?p=4550979#post4550979)

---

