# Ansible

My Ansible configuration

## First startup - macOS

aka. stuff that you need to do manually

[Ansible Docs](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-macos)


1. Install Ansible

```bash
pip3 install ansible
```

> Note: There can be some schenanigans with python packages not being in the `PATH`. In order to fix that look where ansible was installed. On macOS it should be in `~/Library/Python/.../bin`. Check if that path is PATH configured in the .bashrc or .zshrc
> Or just add Python to your PATH: `export PATH="$HOME/Library/Python/3.9/bin:/opt/homebrew/bin:$PATH"`

2. Install required Ansible Galaxy roles

```bash
ansible-galaxy install -r requirements.yml
```

3. Run Ansible

```bash
ansible-playbook main.yml --ask-become-pass
```

Enter your macOS account password when prompted for the "BECOME" password

## Testing configuration

Use Docker for testing if the configuration works fine.
The image uses Ubuntu Focal (not macOS!)

Build Docker image

```bash
./build-docker
```

Run Docker container

```bash
./run-docker
```

To test fully you'll need a [Virtual machine](https://github.com/geerlingguy/mac-osx-virtualbox-vm)

## Tags

These are the avilable tags to run the playbook partially:

- `homebrew` - packages installed using homebrew
- `appstore` - apps installed from AppStore
- `dock` - dock configuration
- `macos` - macOS preferences configuration
- `terminal` - setting up zsh
- `extra-packages` - extra packages that are installed using other packages manager or built from source
- `dotfiles` - dotfiles cloned from separate repository

## Inspired by

Those are the ansible configurations that were an inspiration to mine (aka I've stolen the parts that I liked)

- https://github.com/geerlingguy/mac-dev-playbook
- https://github.com/math0ne/dotfiles/tree/master/playbooks
- https://github.com/ThePrimeagen/ansible

