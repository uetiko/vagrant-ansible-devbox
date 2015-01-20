# vagrant-ansible-devbox
Setup a devbox environment using vagrant and ansible on Virtualbox


Installs Ubuntu devbox with the following

* postgresql 
* postgis
* python development environment
* pip: fabric, Pillow, gunicorn, fogbugz, jira
* nodejs / npm
* git

# setup

1) Install [Virtualbox](https://www.virtualbox.org/wiki/Downloads)

2) Install Ansible:
     
     sudo pip install ansible

3) Install [Vagrant](https://www.vagrantup.com/downloads.html)

4) Download this repository. i.e.:

    cd ~
    git clone https://github.com/radlws/vagrant-ansible-devbox.git
    cd vagrant-ansible-devbox

4b) Edit the Vagrantfile to use 64-bit ubuntu, 32-bit is default. i.e.

    config.vm.box = "ubuntu/trusty32"
    # or
    config.vm.box = "ubuntu/trusty64"

5) Include all required private keys in your ~/.ssh folder starting with the name id_rsa i.e. for bitbucket access.

6) Include shared projects in ~/projects, make the directory it it doesn't exist. Can be empty to start

7) Run: `vagrant up` , when done run `vagrant ssh` 

8) Browse a project. You may start django server using: `manage.py runserver 0.0.0.0:8000` and access it at `localhost:9000` on your host machine. Optionally, run `gunicorn wsgi:application` to start your app.
