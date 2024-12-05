# data2
- name: Creating all the users
  hosts: production
  become: yes
  vars:
    users:
      - username: sakshi
      - username: sneha
      - username: prachi
      - username: diksha

  tasks:
    - name: Creating a group for users
      group:
        name: devops2
        state: present

    - name: Create user "{{ item.username }}"
      user:
        name: "{{ item.username }}"
        create_home: yes
        groups: devops2
        state: present
      loop: "{{ users }}"
