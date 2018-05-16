---?image=assets/images/gitpitch-audience.jpg
@title[Platform Build Lab]
<br><br><br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

#### UEFI Shell Application

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  UEFI Shell Application

  Copyright (c) 2018, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]
<BR>
### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
<br>
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Explain UEFI, the shell, and how they work together </span><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Define the shell components</span><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Use the shell  API  in a UEFI application</span> <br>
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell command Library</span> <br>
 @fa[certificate gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell scripts</span> 


---?image=assets/images/binary-strings-black2.jpg
@title[UEFI Shell Overview Section]
<br><br><br><br><br>
## <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UEFI Shell Overview</span>
<span style="font-size:0.9em" > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Components of the UEFI Shell</span>
  

---?image=/assets/images/slides/Slide4.JPG
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell?]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

Where the Shell sits between the Platform H/w and the OS after all 
   console / devices initialized


What is a UEFI Shell?
	UEFI Application	
	Standardized Command Line Interface for pre-OS
	Sits directly on UEFI firmware (CIRCLE)
	Optimized for small footprint
	Supports rich pre-OS applications
	Standard scripting & API

Versus EFI Shell
	UEFI App
	Same characteristics
	No specification


USE THESE AS BULLETS

+++?image=/assets/images/slides/Slide5.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 02]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

+++?image=/assets/images/slides/Slide6.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 03]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

+++?image=/assets/images/slides/Slide7.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 04]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

+++?image=/assets/images/slides/Slide8.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 05]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

+++?image=/assets/images/slides/Slide9.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[What is a UEFI Shell? 06]
<p align="right"><span class="gold" >What is a UEFI Shell?</span></p>


Note:

Where the Shell sits between the Platform H/w and the OS after all 
   console / devices initialized


What is a UEFI Shell?
	UEFI Application	
	Standardized Command Line Interface for pre-OS
	Sits directly on UEFI firmware (CIRCLE)
	Optimized for small footprint
	Supports rich pre-OS applications
	Standard scripting & API

Versus EFI Shell
	UEFI App
	Same characteristics
	No specification


USE THESE AS BULLETS



---?image=/assets/images/slides/Slide11.JPG
@title[What is a UEFI Shell?]
### <p align="right"><span class="gold" >UEFI Shell Specification V. 2.2</span></p>
<br>
<p align="right"><span style="font-size:0.6em" > <a href="http://www.uefi.org/specsandtesttools"> http://www.uefi.org/specsandtesttools</a></span></p>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<span style="font-size:0.7em" >UEFI Shell v2.0 specification first released 2008 – Latest V2.2 Jan 2016 </span>

Note:


---?image=/assets/images/slides/Slide14.JPG
<!-- .slide: data-transition="none" -->
@title[UEFI Shell Elements]
### <p align="right"><span class="gold" >UEFI Shell Elements</span></p>

Note:

1)Small Size Profiles
Took the UEFI Shell that Intel has been working on as a starting point 4 areas for size

Levels of support
Different levels of support for different usage scenarios and space constraints:
Level 0: No Command-line Interface (CLI). No shell commands. Only shell API.
Level 1: Adds basic scripting support
Level 2: Adds basic commands (cd, cp, mv)
Level 3: Adds interactive CLI
Shell support level can be detected using an environment variable.
Beyond level 3, additional command “profiles” are defined for debug, networking and driver support

2) Shell Commands

Standardized existing usage
Updated for UEFI 2.1+
Standardized argument usage and output
Example some of the grep commands are standardized

3) New Shell API
Smaller executable size – put common functionally back into the shell
Expose previously hidden shell
  capabilities – the shell does some really cool things
– Example to change the current directory (CD) it did not exposes this and no one else could take advantage of this unless they were linked right into it

Execution break support – control “C”

4) Enhanced Scripting
Compatible with existing scripts
Added input redirection & piping
Enhanced if command
   example added capability to use shell without a HD or RAM Drive present. – may not have a HD for Manufacturing 
May not have a Hard drive input output to environment variables



UEFI Advantages = UEFI Shell Advantages
- Flat memory model
- Robust, extensible architecture
- File system, Network, Keyboard, Mouse

- UEFI Works = UEFI Shell Works
- No additional requirements to run

- Write Once/Run Anywhere For Pre-OS
- With standard API/commands = applications from different ISVs work on any platform (Ex: UEFI SCT)




+++?image=/assets/images/slides/Slide15.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Shell Elements 02]
### <p align="right"><span class="gold" >UEFI Shell Elements</span></p>

Note: 

+++?image=/assets/images/slides/Slide16.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Shell Elements 03]
### <p align="right"><span class="gold" >UEFI Shell Elements</span></p>

Note: 

+++?image=/assets/images/slides/Slide17.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[UEFI Shell Elements 04]
### <p align="right"><span class="gold" >UEFI Shell Elements</span></p>

Note: 
1)Small Size Profiles
Took the UEFI Shell that Intel has been working on as a starting point 4 areas for size

Levels of support
Different levels of support for different usage scenarios and space constraints:
Level 0: No Command-line Interface (CLI). No shell commands. Only shell API.
Level 1: Adds basic scripting support
Level 2: Adds basic commands (cd, cp, mv)
Level 3: Adds interactive CLI
Shell support level can be detected using an environment variable.
Beyond level 3, additional command “profiles” are defined for debug, networking and driver support

2) Shell Commands

Standardized existing usage
Updated for UEFI 2.1+
Standardized argument usage and output
Example some of the grep commands are standardized

3) New Shell API
Smaller executable size – put common functionally back into the shell
Expose previously hidden shell
  capabilities – the shell does some really cool things
– Example to change the current directory (CD) it did not exposes this and no one else could take advantage of this unless they were linked right into it

Execution break support – control “C”

4) Enhanced Scripting
Compatible with existing scripts
Added input redirection & piping
Enhanced if command
   example added capability to use shell without a HD or RAM Drive present. – may not have a HD for Manufacturing 
May not have a Hard drive input output to environment variables



UEFI Advantages = UEFI Shell Advantages
- Flat memory model
- Robust, extensible architecture
- File system, Network, Keyboard, Mouse

- UEFI Works = UEFI Shell Works
- No additional requirements to run

- Write Once/Run Anywhere For Pre-OS
With standard API/commands = applications from different ISVs work on any platform (Ex: UEFI SCT)



---?image=/assets/images/slides/Slide19.JPG
@title[Small Size Profiles]


Note:
## Small Size Profiles

Took the UEFI Shell that Intel has been working on as a starting point 4 areas for size

Levels of support
Different levels of support for different usage scenarios and space constraints:

Level 0: No Command-line Interface (CLI). No shell commands. Only shell API.

Level 1: Adds basic scripting support

Level 2: Adds basic commands (cd, cp, mv)

Level 3: Adds interactive CLI

Shell support level can be detected using an environment variable.

Beyond level 3, additional command “profiles” are defined for debug, networking and driver support


---?image=/assets/images/slides/Slide21.JPG
@title[Small Size Profiles detail]
### <p align="right"><span class="gold" >Small Size Profiles</span></p>


Note:
## Small Size Profiles

Different levels; defining a platform confined in a space – go with a smaller profile.  

Took the same shell commands that have always been there and standardized them

Some were never used so were deprecated 

Level 0: provide shell API and that is about it

Level 1: Provide basic scripting support – but not any command line interface so if you want any support then you need to provide the disk itself

Level 2: basic file manipulation commands

Level 3:CLI

Grouped the rest into 3 groups
- UEFI Debug
- Network
- Driver

#### KEY POINT:  Choose the shell that best matches your product needs


---?image=/assets/images/slides/Slide23.JPG
@title[Shell Commands]

Note:

### Shell Commands


---?image=/assets/images/slides/Slide25.JPG
@title[Shell Commands detail]
### <p align="right"><span class="gold" >Shell Commands</span></p>

Note:
### Shell Commands

List of all shell commands from the shell prompt by doing help -b 

Only the commands built with the currenet shell being executed will also be listed in the Help list



---?image=/assets/images/slides/Slide27.JPG
@title[New Shell API]

Note:

### New Shell API


---?image=/assets/images/slides/Slide29.JPG
@title[New Shell API detail]
### <p align="right"><span class="gold" >New Shell API</span></p>

Note:
### New Shell API

This just to give an idea of the over all groups

#### KEY POINT: EFI_SHELL_PROTOCOL is installed on each application image handle

CreateFile, DeleteFile, ReadFile, WriteFile, DeleteFileByName, CloseFile, FindFiles, FindFilesInDir, GetFilePosition, SetFilePosition, GetFileInfo, SetFileInfo, FreeFileList, OpenFileByName, OpenFileList, OpenRoot, OpenRootByHandle, GetFileSize, RemoveDupInFileList


GetMapFromDevicePath, GetFilePathFromDevicePath, GetDevicePathFromFilePath, GetDevicePathFromMap, SetMap, SetAlias, GetEnv, SetEnv, GetCurDir, SetCurDir


Execute, BatchIsActive, IsRootShell


GetPageBreak, EnablePageBreak, DisablePageBreak, GetHelpText, GetDeviceName


Mapping – FS0 instead of full 

---?image=/assets/images/slides/Slide31.JPG
<!-- .slide: data-transition="none" -->
@title[ShellPkg Main Libraries]
### <p align="right"><span class="gold" >ShellPkg Main Libraries</span></p>


Note:

There are three main libraries used by almost all shell commands 


- ShellLib 
  -  Used by both commands and applications. Provides easy access to Shell Protocols, File I/O, and printing to the user. 



- HandleParsingLib
   - Used by both commands and applications. Provides easy access for manipulating handles. This means things like 
conversion the handle to and from the handle index; the index is the 2 digit hex identifier of the handle seen by the user 
sorting of handles to determine parent controllers, child controllers, or which driver controls a given controller 

- ShellCommandLib 
  - fully usable only when linked within the shell binary and therefore only by internal shell commands. This provides extra features for internal commands.





+++?image=/assets/images/slides/Slide32.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[ShellPkg Main Libraries 02]
### <p align="right"><span class="gold" >ShellPkg Main Libraries</span></p>

Note: 

+++?image=/assets/images/slides/Slide33.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[ShellPkg Main Libraries 03]
### <p align="right"><span class="gold" >ShellPkg Main Libraries</span></p>

Note: 


There are three main libraries used by almost all shell commands 


- ShellLib 
  -  Used by both commands and applications. Provides easy access to Shell Protocols, File I/O, and printing to the user. 



- HandleParsingLib
   - Used by both commands and applications. Provides easy access for manipulating handles. This means things like 
conversion the handle to and from the handle index; the index is the 2 digit hex identifier of the handle seen by the user 
sorting of handles to determine parent controllers, child controllers, or which driver controls a given controller 

- ShellCommandLib 
  - fully usable only when linked within the shell binary and therefore only by internal shell commands. This provides extra features for internal commands.



---?image=/assets/images/slides/Slide35.JPG
<!-- .slide: data-transition="none" -->
@title[EDK II ShellPkg]
### <p align="right"><span class="gold" >ShellPkg Main Libraries</span></p>

Note: 


- EDK II native library for shell applications 
  - ShellPkg on Open Source, Repository: https://github.com/tianocore/edk2/tree/master/ShellPkg
- Supports binary portability between EFI Shell 1.0 and UEFI 2.0 shell
- Shell protocols: Calls into UEFI (default) or EFI for functionality
- Shell parameters
  - Handles parameter parsing for flag, value, and position command-line parameters
  - EDK II UEFI Shell 2.0 Library globals in Shell applications
    - #Include <Library/ShellLib.h>
    - gEfiShellParametersProtocol  
    - gEfiShellProtocol

	
+++?image=/assets/images/slides/Slide36.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[EDK II ShellPkg 02]
### <p align="right"><span class="gold" >ShellPkg Main Libraries</span></p>

Note: 


+++?image=/assets/images/slides/Slide37.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[EDK II ShellPkg 03]
### <p align="right"><span class="gold" >ShellPkg Main Libraries</span></p>

Note: 


- EDK II native library for shell applications 
  - ShellPkg on Open Source, Repository: https://github.com/tianocore/edk2/tree/master/ShellPkg
- Supports binary portability between EFI Shell 1.0 and UEFI 2.0 shell
- Shell protocols: Calls into UEFI (default) or EFI for functionality
- Shell parameters
  - Handles parameter parsing for flag, value, and position command-line parameters
  - EDK II UEFI Shell 2.0 Library globals in Shell applications
    - #Include <Library/ShellLib.h>
    - gEfiShellParametersProtocol  
    - gEfiShellProtocol

	
---
@title[Shell Call example]
<p align="center"><span class="gold" >Shell Call Example</span></p>

```C++
// use UEFI shell 2.x interface
//
 if (gEfiShellParametersProtocol != NULL) {
        Argc = gEfiShellParametersProtocol->Argc;
        Argv = gEfiShellParametersProtocol->Argv;
//Create the file with Argv[1] with 
//                 read/write/create
       Status = gEfiShellProtocol->OpenFileByName
          (Argv[1], &Handle, 
           EFI_FILE_MODE_READ | 
           EFI_FILE_MODE_WRITE | 
           EFI_FILE_MODE_CREATE);

// . . .
// Write the buffer data to the file
	Status = gEfiShellProtocol->WriteFile( Handle,     
           (UINTN *)&BufferSize, (void *)Buffer);
```

@[4-5](Parameters Argc and Argv from the command line passed to YOUR shell application)
@[6-8](Create the file with Argv string using the Shell <i>Open File by name</i> function)
@[15-17](After your application is finished with it's task, write the contains using the Shell handle)



Note:

---?image=/assets/images/slides/Slide40.JPG
@title[Enhanced Scripting]

Note: 


---
@title[Enhanced Scripting details]
<br>
<p align="center"><span class="gold" >Shell Enhanced Scripting</span></p>
<br>
 @fa[circle gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;Contains <b>.nsh</b> extention</span> <br>
 @fa[circle gp-bullet-gold]<span style="font-size:0.9em">&nbsp;&nbsp;"Startup.nsh" runs first</span> <br>
 @fa[circle gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Supports:</span><br>
 <span style="font-size:0.6em">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&check;&nbsp;&nbsp;Command-line arguments</span><br>
 <span style="font-size:0.6em">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&check;&nbsp;&nbsp;Standard script commands</span> <br>
 <span style="font-size:0.6em">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&check;&nbsp;&nbsp;Input & output redirection & pipes</span><br>
 

Note: 
- Text files with .nsh extension are shell scripts
- Supports command-line arguments using positional parameters %0 - %9 and shift.
- Supports standard script commands 
  - if/else/endif
  - goto
  - for/endfor
  - echo
  - exit
- Supports input & output redirection & pipes.
- Can also redirect to/from environment variables!


- Startup.nsh – First Shell script can be on any FS system. the first script run by the UEFI Shell and it can be run from any removable device


---?image=/assets/images/slides/Slide43.JPG
@title[Shell Scripts (Benefits)]
<br>
<p align="center"><span class="gold" >Shell Scripts (Benefits)</span></p>

Note: 

The UEFI Shell can execute commands from a file, which is called a batch script file (.nsh files). 


### Benefits: These files allow users to simplify routine or repetitive tasks. 
- Perform basic flow control. 
- Allow branching and looping in a script. 
- Allow users to control input and output and call other batch programs (known as script nesting). 



---
@title[Script Detects Shell Capabilities]
<br>
<p align="center"><span class="gold" >Script Detects Shell Capabilities</span></p>
<br>
```shell
# check if Shell supports level 3 commands
 # Exit on error
 if %uefishellsupport% ult 3 then
   echo Must support UEFI Shell, Level 3
   exit /b 2
 endif

 # check that Shell supports Debug1 profile.
 if profiles(Debug1)then
   echo UEFI Shell supports Debug1 profile
 endif
```

@[2-4](Check if Shell supports level 3 commands - "ult" is <u>u</u>nsigned <u>l</u>ess <u>t</u>han)
@[9-10](Check that Shell supports Debug1 profile.)



Note:
Walk through the code

The ULT is unsigned/less than

---
@title[UEFI Shell Script Example]
<br>
<p align="center"><span class="gold" >UEFI Shell Script Example</span></p>
<br>
<span style="font-size:0.7em"><font color="yellow">Script1.nsh</font></span>
```shell
# Simple UEFI Shell script file
echo  -off
script2.nsh
if exist %cwd%Mytime.log then
     type Mytime.log
endif
echo "%HThank you.” “%VByeBye:) %N"
```
<br>
<span style="font-size:0.7em"><font color="yellow">Script2.nsh</font></span>
```shell
# Show nested scripts
time > Mytime.log
for %a run (3 1 -1)
    echo %a counting down
endfor
```


---?image=/assets/images/slides/Slide47.JPG
@title[Documentation for EDK II ShellPkg]
<p align="center"><span class="gold" >Documentation for EDK II ShellPkg</span></p>
<br>
<br>
<br>
 @fa[book-open gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;Documenation Link:<br> &nbsp;&nbsp;&nbsp;&nbsp;<a href="https://github.com/tianocore/tianocore.github.io/wiki/ShellPkg">wiki Shell Package</a></span>


Note:

UEFI Shell Documentation updated in the Engineering Resources section


---?code=Sample/MyShellApp/MyShellApp.c&lang=c++&title=UEFI Shell 2.2   &nbsp;&nbsp;Vs.   &nbsp;&nbsp;EFI Shell 1.0


Note:

This slide shows how to access UEFI Shell 2.0 Versus EFI Shell 1.0
There are 2 different GUIDs 
Simply try to open one GUID verse the other to see which Shell is currently in use.


+++?code=Sample/MyShellApp/MyShellApp.c&lang=c++&title=UEFI Shell 2.2   &nbsp;&nbsp;Vs.   &nbsp;&nbsp;EFI Shell 1.0

@[70-79](check input parameters from command line using UEFI Shell 2.2)
@[81-82](No error so assign Argc & Argv from Shell 2.2)
@[85-92](Else, check if EFI Shell 1.0 )
@[96-97](No error so assign Argc & Argv from Shell 1.0)
@[99-100](Else, Error out of application  )

Note:

This slide shows how to access UEFI Shell 2.0 Versus EFI Shell 1.0
There are 2 different GUIDs 
Simply try to open one GUID verse the other to see which Shell is currently in use.






---?image=/assets/images/slides/Slide52.JPG
@title[Legacy vs. UEFI ]

### <p align="right"><span class="gold" >Legacy vs. UEFI</span></p>

Note:
The UEFI SHELL is an UEFI application that allows you to interface with the UEFI environment prior to the time the OS is loaded. Once the OS starts loading, the UEFI environment is no longer accessible through the Shell. 
The UEFI Shell supports a command line interface similar to DOS or Unix.  In fact a lot of the same commands exist in the UEFI shell that are in DOS and forms of Linux.



---?image=/assets/images/slides/Slide54.JPG
@title[Shell Usage ]
### <p align="right"><span class="gold" >Shell Usage</span></p>

Note:
The shell is where preboot programs  will execute.  For example, manufacturing test applications with the rich pre boot environment there is no need to run / execute an operating system
Typical environment that an EFI application might need to execute pre-operating system functions:

- Execute preboot programs
- update programs
- disk utilities
- tests(hwd and soft)
- operating system installation – Configuration utility of a Driver
- Diagnostics
- Platform Testing & Driver Diagnostics

- Move files around between different devices (hard disk, CD/DVD, USB flash drives, …)
- The shell is where files can be moved around just as in DOS or Unix.

- Load a preboot UEFI driver in the system (.efi)
- The shell is where preboot EFI drivers are loaded in the system such as a lan stack tcpip drivers, update old drivers in flash, new drivers for plugin cards etc.
 

- LAN stack & TCP/IP drivers
- Update old drivers in flash
- New drivers for plug-in cards

---?image=/assets/images/slides/Slide56.JPG
@title[Accessing the Shell]
### <p align="right"><span class="gold" >Accessing the Shell</span></p>

Note:
Boot UEFI Shell from FAT/FAT32 partition:
1.  Special boot file located under /EFI/boot/ directory:
    - BOOTia32.efi (IA32) or BOOTx64.efi (x64) or other NON IA



---?image=/assets/images/slides/Slide58.JPG
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path]

<p align="left"><span class="gold" >UEFI File System & Device Path</span></p>


Note:
Can manipulate only UEFI system partitions (FAT/FAT32) where boot loader and UEFI applications are located:

An example of the EFI File system is best seen using the MAP Command that will display the mappings in nvram between block devices .  
The EFI shell is replacing what is to the left of the “:” with the device path to the right of the “:”


- Blkxx designates a raw block device 
- Such as a disk controller, floppy controller etc.
- FSy designates that a block device has a fat file system on that device.
- The Map command displays all the raw block devices in the system and the FAT file systems mounted and usable.
- After the colon is the device path or physical location of where that device or file system is located.


- Lets try the Map Command on your classroom systems.


+++?image=/assets/images/slides/Slide60.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 02]
<br>
<p align="left"><span class="gold" >UEFI File System & Device Path</span></p>

Note:


+++?image=/assets/images/slides/Slide61.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 03]
<br>
<p align="left"><span class="gold" >UEFI File System & Device Path</span></p>

Note:

+++?image=/assets/images/slides/Slide62.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 04]
<br>
<p align="left"><span class="gold" >UEFI File System & Device Path</span></p>

Note:

+++?image=/assets/images/slides/Slide63.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 05]
<br>
<p align="left"><span class="gold" >UEFI File System & Device Path</span></p>

Note:

+++?image=/assets/images/slides/Slide64.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 06]
<br>
<p align="left"><span class="gold" >UEFI File System & Device Path</span></p>

Note:

+++?image=/assets/images/slides/Slide65.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 07]
<br>
<p align="left"><span class="gold" >UEFI File System & Device Path</span></p>

Note:


+++?image=/assets/images/slides/Slide66.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->	 
@title[UEFI File System & Device Path 08]
<br>
<p align="left"><span class="gold" >UEFI File System & Device Path</span></p>

Note:
Can manipulate only UEFI system partitions (FAT/FAT32) where boot loader and UEFI applications are located:

An example of the EFI File system is best seen using the MAP Command that will display the mappings in nvram between block devices .  
The EFI shell is replacing what is to the left of the “:” with the device path to the right of the “:”


- Blkxx designates a raw block device 
- Such as a disk controller, floppy controller etc.
- FSy designates that a block device has a fat file system on that device.
- The Map command displays all the raw block devices in the system and the FAT file systems mounted and usable.
- After the colon is the device path or physical location of where that device or file system is located.


- Lets try the Map Command on your classroom systems.


---  
@title[Summary]
##### <p align="center"<span class="gold"   >Summary </span></p><br>
<br>
 @fa[certificate gp-bullet-green]<span style="font-size:0.9em">&nbsp;&nbsp;Explain UEFI, the shell, and how they work together </span><br>
 @fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Define the shell components</span><br>
 @fa[certificate gp-bullet-yellow]<span style="font-size:0.9em">&nbsp;&nbsp;Use the shell  API  in a UEFI application</span> <br>
 @fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell command Library</span> <br>
 @fa[certificate gp-bullet-ltgreen]<span style="font-size:0.9em">&nbsp;&nbsp;UEFI Shell scripts</span> 

 

---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/Questions.png =10x) 


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)


---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2018, Intel Corporation. All rights reserved.
**/

```