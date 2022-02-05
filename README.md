# Youtube-Viewer
!!! This program is not 100% complete yet and may contain errors!!!

A youtube viewer, which connects to freely available proxy servers beforehand. The proxies are obtained from the following URL 'https://free-proxy-list.net/'.

The program goes through several iterations, with one iteration calling a video 30-40 times. After each iteration, the program looks for a new proxy server through which it can call up the video.
After each video call, it is checked whether more than 15% CPU and memory are available and only then does the next window open. This is to control the resources used. (The limit values (can be adjusted in line 31).
Optionally, it can be set that after the iterations have been run through, an entry is made in the Excel file "test.xlss", which includes the duration of the program, the video calls, the video URL, etc.

## Features
      • access via proxy
      • resource control
      • documentation in xlsx

## Setup

### Install requirements
```bash
pip install -r requirements.txt
```

Chrome driver is also required: https://chromedriver.chromium.org

### viewer.py
In Line 12 can be set if the data should be saved in the Excel file.
```python
useXlxs = False
```

## Start Program
```bash
python viewer.py
```

After you started the programm you will be asked for the Url, number of iterations, search for specific country, kill time for the videos and the current views. Set your params
here. If you want to search for a specific country you will be asked for the country code here. Set here for example "GB" if you only want Proxies from Great Britain or "US" for 
United States and so on.

You can find a list of all codes here under Alpha-2-code : https://www.iban.com/country-codes


The number of the iteration is between 30-40, because it can happen that a proxy is used several times and thus attempts are made to imitate user behavior.
```bash
"URL:"
"Iterations (1 Iteration = 30-40 Tabs):"
"Do you want to search for proxies in a specific country? (y/n):"
"Kill-Time:"
"Current-Views:"
```
Now it will search for proxies until it finds a working one.
```bash
Start Iteration 0
Proxy    103.234.98.140:8888    doesnt work
Proxy    209.141.55.228:80    doesnt work
Proxy    161.35.4.201:80    doesnt work
Proxy    103.214.109.69:80    doesnt work
Proxy    47.243.135.104:8080    doesnt work
Proxy    163.116.136.116:8081    doesnt work
Proxy    167.114.96.27:9300    work                <-- use this
```

It will check your memory and cpu and if more than 15% are available a step will be processed. If not it will wait until space is available.
```bash
Free Memory: 37.33941134252943%
Free Cpu: 97.0%
Step 1 from 38 | Iteration: 1 from 1
Free Memory: 35.60870452165333%
Free Cpu: 92.5%
Step 2 from 38 | Iteration: 1 from 1
Free Memory: 35.126594765932%
Free Cpu: 89.7%
Step 3 from 38 | Iteration: 1 from 1
...
```

After all tabs have been opened, it waits until the previously entered time expires (killTime) and then all windows are closed again.

## Updates
v1.0 = initialisation
v1.1 = country code filter


- last Update: 05.02.2022 - DD.MM.YYYY
