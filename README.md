# MeetupDec2020

Accelerate Journey to AI on IBM LinuxOne. CP4D Meetup.

## Steps to be used by users/attendees of meetup

(1) If the port 8888 is in use by some old process, use the following to find the process id of the process that is using the port 8888 and kill that process if you don't need that process.

    (A) On Mac laptop: Get the process ID of the process using the command:
      `lsof -i ':8888' | awk '{print $2}'`
      Kill the process using `kill <PID>` where <PID> is obtained from the previous command.

    (B) On Linux laptop: Get the process ID of the process using the command:
      `sudo netstat -tulpn | grep ':8888' | awk '{print $NF}'`
      Kill the process using 'kill <PID>' where <PID> is obtained from the previous command.

    (C) On Windows laptop: Get the process ID of the process using the command in the cmd prompt:
      `netstat -ano | findstr :8888`
      The PID will be in the last column in the output. Replace <PID> with that in the following command to kill that process:
      `taskkill /PID <PID> /F`

(2) Create ssh tunnel and login to remote 'Linux on Z' VM

    (A) On Mac or Linux laptop terminal,
      (i) run the command to create ssh tunnel: `ssh -N -f -L localhost:8888:localhost:8889 linux1@<VM_IP>`. <VM_IP> is the IP of the `Linux on Z` VM. Enter password at the password prompt.
      (ii) run the command to login to the remote `Linux on Z` VM: `ssh linux1@<VM_IP>`. Enter password at the password prompt and you would be logged in to the Linux on Z machine.

    (B) On Windows laptop, download putty if not already installed.
       (i) Launch putty. Go to `Session`, enter `linux1@<VM_IP>`. <VM_IP> is the IP of the `Linux on Z` VM.
       (ii) Select `Connection > SSH > Tunnels`
       (iii) At `Add new forwarded port:`, enter 8888 as `Source port` and `localhost:8889` as Destination.
       (iv) Click `Add`
       (v) Select the newly added line in the bigger box on the same page by clicking on the line
       (vi) Click `Open`.
       (vii) Enter password at the password prompt and you would be logged in to the `Linux on Z` machine/VM.

(3) On the remote `Linux on Z` machine, follow the steps from the /home/linux1/README.md file.

