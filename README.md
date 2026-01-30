# AAE5303 Environment Setup Report

> **Important:** Follow this structure exactly in your submission README.  
> Your goal is to demonstrate **evidence, process, problem-solving, and reflection** — not only screenshots.

---

## 1. System Information

**Laptop model:**  
_Lenovo ThinkPad T14P_

**CPU / RAM:**  
_Intel Core U9-285H, 32GB RAM_

**Host OS:**  
_Ubuntu 22.04_

**Linux/ROS environment type:**  
_[Choose one:]_
- [ ] Dual-boot Ubuntu
- [ ] WSL2 Ubuntu
- [√] Ubuntu in VM (UTM/VirtualBox/VMware/Parallels)
- [ ] Docker container
- [ ] Lab PC
- [ ] Remote Linux server

---

## 2. Python Environment Check

### 2.1 Steps Taken

Describe briefly how you created/activated your Python environment:

**Tool used:**  
_venv_

**Key commands you ran:**
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

**Any deviations from the default instructions:**  
_None_

### 2.2 Test Results

Run these commands and paste the actual terminal output (not just screenshots):

```bash
(.venv) root@c50dcdd54c88:~/aae5303-env-check# python scripts/run_smoke_tests.py
```

**Output:**
```

========================================
AAE5303 One-command Environment Check
Tip: read README.md for interpretation and fixes.
========================================


========== Step 1: Python + ROS environment checks ==========
Running: /root/aae5303-env-check/.venv/bin/python -u /root/aae5303-env-check/scripts/test_python_env.py
========================================
AAE5303 Environment Check (Python + ROS)
Goal: help you verify your environment and understand what each check means.
========================================

Step 1: Environment snapshot
  Why: We capture platform/Python/ROS variables to diagnose common setup mistakes (especially mixed ROS env).
Step 2: Python version
  Why: The course assumes Python 3.10+; older versions often break package wheels.
Step 3: Python imports (required/optional)
  Why: Imports verify packages are installed and compatible with your Python version.
Step 4: NumPy sanity checks
  Why: We run a small linear algebra operation so success means more than just `import numpy`.
Step 5: SciPy sanity checks
  Why: We run a small FFT to confirm SciPy is functional (not just installed).
Step 6: Matplotlib backend check
  Why: We generate a tiny plot image (headless) to confirm plotting works on your system.
Step 7: OpenCV PNG decoding (subprocess)
  Why: PNG decoding uses native code; we isolate it so corruption/codec issues cannot crash the whole report.
Step 8: Open3D basic geometry + I/O (subprocess)
  Why: Open3D is a native extension; ABI mismatches can segfault. Subprocess isolation turns crashes into readable failures.
Step 9: ROS toolchain checks
  Why: The course requires ROS tooling. This check passes if ROS 2 OR ROS 1 is available (either one is acceptable).
  Action: building ROS 2 workspace package `env_check_pkg` (this may take 1-3 minutes on first run)...
  Action: running ROS 2 talker/listener for a few seconds to verify messages flow...
Step 10: Basic CLI availability
  Why: We confirm core commands exist on PATH so students can run the same commands as in the labs.

=== Summary ===
✅ Environment: {
  "platform": "Linux-6.8.0-90-generic-x86_64-with-glibc2.35",
  "python": "3.10.12",
  "executable": "/root/aae5303-env-check/.venv/bin/python",
  "cwd": "/root/aae5303-env-check",
  "ros": {
    "ROS_VERSION": "2",
    "ROS_DISTRO": "humble",
    "ROS_ROOT": null,
    "ROS_PACKAGE_PATH": null,
    "AMENT_PREFIX_PATH": "/opt/ros/humble",
    "CMAKE_PREFIX_PATH": null
  }
}
✅ Python version OK: 3.10.12
✅ Module 'numpy' found (v2.2.6).
✅ Module 'scipy' found (v1.15.3).
✅ Module 'matplotlib' found (v3.10.8).
✅ Module 'cv2' found (v4.13.0).
✅ Module 'rclpy' found (vunknown).
✅ numpy matrix multiply OK.
✅ numpy version 2.2.6 detected.
✅ scipy FFT OK.
✅ scipy version 1.15.3 detected.
✅ matplotlib backend OK (Agg), version 3.10.8.
✅ OpenCV OK (v4.13.0), decoded sample image 128x128.
✅ Open3D OK (v0.19.0), NumPy 2.2.6.
✅ Open3D loaded sample PCD with 8 pts and completed round-trip I/O.
✅ ROS 2 CLI OK: /opt/ros/humble/bin/ros2
✅ ROS 1 detected: rosversion -d -> humble
✅ colcon found: /usr/bin/colcon
✅ ROS 2 workspace build OK (env_check_pkg).
✅ ROS 2 runtime OK: talker and listener exchanged messages.
✅ Binary 'python3' found at /root/aae5303-env-check/.venv/bin/python3

All checks passed. You are ready for AAE5303 🚀
✅ Python + ROS environment checks: PASS (15.5s)

========== Step 2: Open3D point cloud pipeline ==========
Running: /root/aae5303-env-check/.venv/bin/python -u /root/aae5303-env-check/scripts/test_open3d_pointcloud.py
ℹ️ Loading /root/aae5303-env-check/data/sample_pointcloud.pcd ...
✅ Loaded 8 points.
   • Centroid: [0.025 0.025 0.025]
   • Axis-aligned bounds: min=[0. 0. 0.], max=[0.05 0.05 0.05]
✅ Filtered point cloud kept 7 points.
✅ Wrote filtered copy with 7 points to /root/aae5303-env-check/data/sample_pointcloud_copy.pcd
   • AABB extents: [0.05 0.05 0.05]
   • OBB  extents: [0.08164966 0.07071068 0.05773503], max dim 0.0816 m
🎉 Open3D point cloud pipeline looks good.
✅ Open3D point cloud pipeline: PASS (2.9s)

ℹ️ Cleaned up 1 generated file(s) in data/.

========================================
OVERALL RESULT: PASS
========================================

```

```bash
python scripts/test_open3d_pointcloud.py
```

**Output:**
```
Running: /root/aae5303-env-check/.venv/bin/python -u /root/aae5303-env-check/scripts/test_open3d_pointcloud.py
ℹ️ Loading /root/aae5303-env-check/data/sample_pointcloud.pcd ...
✅ Loaded 8 points.
   • Centroid: [0.025 0.025 0.025]
   • Axis-aligned bounds: min=[0. 0. 0.], max=[0.05 0.05 0.05]
✅ Filtered point cloud kept 7 points.
✅ Wrote filtered copy with 7 points to /root/aae5303-env-check/data/sample_pointcloud_copy.pcd
   • AABB extents: [0.05 0.05 0.05]
   • OBB  extents: [0.08164966 0.07071068 0.05773503], max dim 0.0816 m
🎉 Open3D point cloud pipeline looks good.
✅ Open3D point cloud pipeline: PASS (2.9s)

ℹ️ Cleaned up 1 generated file(s) in data/.
```

**Screenshot:**  
<img width="1056" height="1026" alt="test" src="https://github.com/user-attachments/assets/ecea2879-78f0-4e38-a02b-d1158e3930fc" />

---

## 3. ROS 2 Workspace Check

### 3.1 Build the workspace

Paste the build output summary (final lines only):

```bash
source /opt/ros/humble/setup.bash
colcon build --packages-select env_check_pkg
```

**Expected output:**
```
Summary: 1 package finished [x.xx s]
```

**Your actual output:**
```
Starting >>> env_check_pkg
Finished <<< env_check_pkg [0.26s]                  

Summary: 1 package finished [0.57s]

```

### 3.2 Run talker and listener

Show both source commands:

```bash
source /opt/ros/humble/setup.bash
source install/setup.bash
```

**Then run talker:**
```bash
ros2 run env_check_pkg talker.py
```

**Output (3–4 lines):**
```
[INFO] [1769770908.677073899] [env_check_pkg_talker]: AAE5303 talker ready (publishing at 2 Hz).
[INFO] [1769770909.178005126] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #0'
[INFO] [1769770909.677656485] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #1'
[INFO] [1769770910.178224295] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #2'
[INFO] [1769770910.677921158] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #3'
```

**Run listener:**
```bash
ros2 run env_check_pkg listener.py
```

**Output (3–4 lines):**
```
[INFO] [1769771130.371938475] [env_check_pkg_listener]: AAE5303 listener awaiting messages.
[INFO] [1769771142.017851759] [env_check_pkg_listener]: I heard: 'AAE5303 hello #0'
[INFO] [1769771142.520852877] [env_check_pkg_listener]: I heard: 'AAE5303 hello #1'
[INFO] [1769771143.016114810] [env_check_pkg_listener]: I heard: 'AAE5303 hello #2'
[INFO] [1769771143.518120237] [env_check_pkg_listener]: I heard: 'AAE5303 hello #3'
```

**Alternative (using launch file):[√]**
```bash
ros2 launch env_check_pkg env_check.launch.py
```

**Output (3–4 lines):**
```
[INFO] [launch]: All log files can be found below /root/.ros/log/2026-01-30-18-23-00-912177-c50dcdd54c88-369
[INFO] [launch]: Default logging verbosity is set to INFO
[INFO] [talker-1]: process started with pid [370]
[INFO] [listener-2]: process started with pid [372]
[listener-2] [INFO] [1769768581.000035453] [env_check_pkg_listener]: AAE5303 listener awaiting messages.
[talker-1] [INFO] [1769768581.000753065] [env_check_pkg_talker]: AAE5303 talker ready (publishing at 2 Hz).
[talker-1] [INFO] [1769768581.502015683] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #0'
[listener-2] [INFO] [1769768581.502883640] [env_check_pkg_listener]: I heard: 'AAE5303 hello #0'
[talker-1] [INFO] [1769768582.001327289] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #1'
[listener-2] [INFO] [1769768582.001871478] [env_check_pkg_listener]: I heard: 'AAE5303 hello #1'
[talker-1] [INFO] [1769768582.501655598] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #2'
[listener-2] [INFO] [1769768582.502207767] [env_check_pkg_listener]: I heard: 'AAE5303 hello #2'
[talker-1] [INFO] [1769768583.001032573] [env_check_pkg_talker]: Publishing: 'AAE5303 hello #3'
[listener-2] [INFO] [1769768583.001897496] [env_check_pkg_listener]: I heard: 'AAE5303 hello #3'
```
**Screenshot:**  
_<img width="982" height="286" alt="talker_listener" src="https://github.com/user-attachments/assets/2fcef2c6-d4a5-4f30-8a37-318638cc83e1" />


---

## 4. Problems Encountered and How I Solved Them

> **Note:** Write 2–3 issues, even if small. This section is crucial — it demonstrates understanding and problem-solving.

### Issue 1: [Fail to pass smoke_test]

**Cause / diagnosis:**  
1.Didn't install enough needed dependings   
2.Did't build workspace in docker

**Fix:**  
Build workspace before or install dependings again

```bash
colcon build --packages-select env_check_pkg
```

**Reference:**  

_myself_

---

### Issue 2: [Fail to build ROS 2 workspace]

**Cause / diagnosis:**  
Error：Could not find ament_cmake package.The lack of ament_cmake package leads to the CMakeLists.txt of env_check_pkg fail to find the ROS 2 compilation toolchain

**Fix:**  
_install the package and build again_

```bash
apt install -y ros-humble-ament-cmake ros-humble-rclcpp ros-humble-std-msgs
cd /root/aae5303-env-check/ros2_ws
source /opt/ros/humble/setup.bash
colcon build --packages-select env_check_pkg
```

**Reference:**  
_AI assistant_

---

### Issue 3 (Optional): [no internet]

**Cause / diagnosis:**  
Don't have internet to clone github _

**Fix:**  
restart my network card and get ip again_

```bash
ip addr show
sudo ip link set ens33 up
sudo dhclient ens33
```

**Reference:**  
_AI assistant_

---

## 5. Use of Generative AI (Required)

Choose one of the issues above and document how you used AI to solve it.

> **Goal:** Show critical use of AI, not blind copying.

### 5.1 Exact prompt you asked

**Your prompt:**
```
在vmware中使用Ubuntu22.04时，桥接模式已开启，但是没有网络
```

### 5.2 Key helpful part of the AI's answer

**AI's response (relevant part only):**
```
桥接模式无网络的常见原因：VMware 虚拟网卡未启用 → Ubuntu 网络配置未自动获取IP → 防火墙/网络服务异常 → VMware 桥接驱动问题，按顺序排查即可。
```

### 5.3 What you changed or ignored and why

Explain briefly:
- Did the AI recommend something unsafe?
- Did you modify its solution?
- Did you double-check with official docs?

**Your explanation:**  
_ignored(unsafe): AI told me to close the fire wall to connet with the network in windows system _

### 5.4 Final solution you applied

Show the exact command or file edit that fixed the problem:

```bash
ip addr show
sudo ip link set ens33 up
sudo dhclient ens33
```

**Why this worked:**  
_It mainly equals to reopen thenetwork card and get new ip address._

---

## 6. Reflection (3–5 sentences)

Short but thoughtful:

- What did you learn about configuring robotics environments?
- What surprised you?
- What would you do differently next time (backup, partitioning, reading error logs, asking better AI questions)?
- How confident do you feel about debugging ROS/Python issues now?

**Your reflection:**

_Every time before using ros2 have to build workspce at the beginning.
Actually I set up those enviornment mainly by myself by using cmd in terminal in vmware,
So i'm quiet proficient to find out and solve problems._

---

## 7. Declaration

✅ **I confirm that I performed this setup myself and all screenshots/logs reflect my own environment.**

**Name:**  
_[Zeng xincheng]_

**Student ID:**  
_[25097041G]_

**Date:**  
_[2026/1/30]_

---

## Submission Checklist

Before submitting, ensure you have:

- [√] Filled in all system information
- [√] Included actual terminal outputs (not just screenshots)
- [√] Provided at least 2 screenshots (Python tests + ROS talker/listener)
- [√] Documented 2–3 real problems with solutions
- [√] Completed the AI usage section with exact prompts
- [√] Written a thoughtful reflection (3–5 sentences)
- [√] Signed the declaration

---

**End of Report**
