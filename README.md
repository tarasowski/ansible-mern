# ansible-mern
Mern stack with ansible

```yml
---
- hosts: your_ec2_ip
  become: yes
  tasks:
    - name: Update package lists
      apt:
        update_cache: yes

    - name: Install Node.js and npm
      apt:
        name: nodejs
        state: present

    - name: Install MongoDB
      apt:
        name: mongodb
        state: present

    - name: Clone React application from Git
      git:
        repo: 'your_git_repo_url'
        dest: /home/ubuntu/myapp

    - name: Install application dependencies
      command: npm install
      args:
        chdir: /home/ubuntu/myapp

    - name: Start application
      command: npm start
      args:
        chdir: /home/ubuntu/myapp # Ansible will change the current working directory to /home/ubuntu/myapp on the target hosts before executing the rest of the tasks in the playbook.
...
```
