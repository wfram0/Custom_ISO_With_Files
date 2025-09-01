# How to make a custom ISO

## Tools
You will need a few tools to make this happen
1. OSCDIMG

        You will need to install the Windows ADK (Deployment Tools only)
     **Install it at: https://go.microsoft.com/fwlink/?linkid=2289980**

## Commands

`To avoid any issues, run CMD as Administrator`

### ***Change Directory to `C:\`***
<pre><code>cd /d C:\</code></pre>


### ***Create working folder***
<pre><code>mkdir C:\FileISO\CustomFiles
</code></pre>

`Save data you want to add to the Windows ISO in the CustomFiles folder`

oscdimg WILL fail if C:\FileISO doesn't exist

### ***Generate ISO File***
<pre><code>"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\amd64\Oscdimg\oscdimg.exe" -m -o -u2 -b"C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\amd64\Oscdimg\etfsboot.com" "C:\FileISO\CustomFiles" "C:\FileISO\output.iso"</code></pre>

#### Command Explanation
***-m***: Allows the final ISO file to be larger than `700MB`

***-o***: Optimizes file size by trying to encode duplicates

***-u2***: Use `Joliet` directory structure (support Unicode and longer file names)

***-b***: Makes the final ISO bootable

### ***Clean Up***
<pre><code>rd /s /q C:\FileISO\CustomFiles</code></pre>

### Finished ISO
You will find the completed ISO file under `C:\FileISO`