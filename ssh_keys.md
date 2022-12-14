# Adding ssh keys
1. Run this on your local machine to generate key paris `ssh-keygen -f rsa -C new_user`
3. Run this on the server to create the user `sudo adduser -m new_user`
4. Add the user to sudoers on the server `sudo usermod -aG sudo username` or `sudo visudo -f /etc/sudoers` and append `new_user ALL=(ALL)  NOPASSWD:ALL`
5. Login `sudo su - new_user`
6. Create a .ssh dir and add keys 
   ```
   mkdir .ssh
   chmod 700 .ssh
   cd .ssh
   touch authorized_keys
   chmod 600 authorized_keys
   cat rsa.pub >> authorized_keys
   ```
7. Finally you can ssh to the system without password. Just with the ssh private key -
   ```
   ssh -i rsa new_user@domain_name
   ```
