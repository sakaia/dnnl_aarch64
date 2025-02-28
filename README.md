# DNNL_aarch64 ; Deep Neural Network Library for AArch64

## Abstract

- Deep Neural Network Libary for AArch64 (DNNL_aarch64) is an open-source performance library for deep learning application running on ARM(R)v8-A architecture CPUs.
- DNNL_aarch64 is a port of Deep Neural Network Library (DNNL) developed by Intel(R) aiming to speed up deep learning on x86_64 CPUs.
- DNNL_aarch64 is being customized to ARMv8-A architecture with the Scalable Vector Extension (SVE).
- One of the key components of Intel's DNNL is x86_64 JIT assembler 'Xbayk', which is developed by Shigeo MITSUNARI (Cybozu Labs Inc.).
To use same performance tuning technique, DNNL_aarch64 includes ARMv8-A JIT assembler 'Xbyak_aarch64'. 

## Feature

- DNNL_aarch64 is based on DNNL v0.19, which was called MKL-DNN.

## Development status

Intel's original DNNL has varios operation kernels of deep learning, such as batch_normalization, concat, convolution, deconvolution, eltwise, pooling, reorder, rnn_forward, shuffle, softmax, sum.
Intel has tuned these operation kernels by using JIT assembler 'Xbyak'.
We are applying same technique to DNNL_aarch64 with 'Xbyak_aarch64' in order to improve performance of operation kernels running on ARMv8-A CPUs,
but only reorder kernel has been JIT-ed. The other kernels are currently under development.
If you use the other kernels of DNNL_aarch64, reference C++ implementation is used. They output correct result, but run somewhat slow.

DNNL includes the following example and test programs, which are built in "YOUR_BUILD_DIRECTORY/examples" and "YOUR_BUILD_DIRECTORY/tests/gtests" directories.
DNNL_aarch64 also contains the same programs. You can run them on ARMv8-a enviroment.

- simple-net-c
- simple-net-cpp
- simple-rnn-cpp
- simple-rnn-training-cpp
- simple-training-net-c
- simple-training-net-cpp
- test_batch_normalization_f32
- test_batch_normalization_s8
- test_concat
- test_convolution_backward_data_f32
- test_convolution_backward_data_s16s16s32
- test_convolution_backward_weights_f32
- test_convolution_backward_weights_s16s16s32
- test_convolution_eltwise_forward_f32
- test_convolution_eltwise_forward_x8s8f32s32
- test_convolution_format_any
- test_convolution_forward_f32
- test_convolution_forward_s16s16s32
- test_convolution_forward_u8s8fp
- test_convolution_forward_u8s8s32
- test_deconvolution
- test_eltwise
- test_gemm_f32
- test_gemm_s8s8s32
- test_gemm_s8u8s32
- test_iface_attr
- test_iface_pd_iter
- test_inner_product_backward_data
- test_inner_product_backward_weights
- test_inner_product_forward
- test_lrn_backward
- test_lrn_forward
- test_memory
- test_mkldnn_threading
- test_pooling_backward
- test_pooling_forward
- test_reorder
- test_rnn_forward
- test_shuffle
- test_softmax_backward
- test_softmax_forward
- test_sum

You can execute DNNL_aarch64 on systems using Arm(R)v8-A architecure CPUs supporting SVE instructions.
Even if you can't access such systems, you can try DNNL_aarch64 on QEMU (generic and open source machine emulator and virtualizer).

We have partially checked that programs built with DNNL_aarch64 can be executed with qemu version 3.1.0 or higher on Linux running on x86_64 CPUs.
The following dpkgs are required.

* binutils-aarch64-linux-gnu
* cpp-8-aarch64-linux-gnu
* cpp-aarch64-linux-gnu
* g++-8-aarch64-linux-gnu
* g++-aarch64-linux-gnu
* gcc-8-aarch64-linux-gnu
* gcc-8-aarch64-linux-gnu-base:amd64
* gcc-aarch64-linux-gnu
* pkg-config-aarch64-linux-gnu
* qemu
* qemu-block-extra:amd64
* qemu-system-arm
* qemu-system-common
* qemu-system-data
* qemu-system-gui
* qemu-user
* qemu-user-static
* qemu-utils

## Requirements

- Currently, DNNL_aarch64 is intended to run on CPUs of ARMv8-A with SVE. If you run DNNL_aarch64 on CPUs without SVE, it will be aborted because of undefined instruction exception. 

- Otherwise, qemu version 3.1.0 or higher. We have partially checked that programs built with DNNL_aarch64 can be executed with qemu version 3.1.0 or higher on Linux runnign on x86_64 CPUs.

## Installation

Download DNNL_aarch64 source code or clone the repository.

```
git clone https://github.com/fujitsu/dnnl_aarch64.git
```

Then, please follow the installation instruction written in [mkl-dnn/README.md](mkl-dnn/README.md).

If you want to use qemu, please follow the instruction which is wrtten in dnnl_aarch64/tools/replace.sh.

```
cd YOUR_BUILD_DIRECTORY
REPOSITORY_DIRECTORY_YOU_DOWNLOADED/dnnl_aarch64/tools/replace.sh
```


## License

Copyright FUJITSU LIMITED 2019

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Notice

* Arm is a registered trademark of Arm Limited (or its subsidiaries) in the US and/or elsewhere.
* Intel is a registered trademark of Intel Corporation (or its subsidiaries) in the US and/or elsewhere.

## History

|Date|Version|Remarks|
|----|----|----|
|December 11, 2019|0.9.0_base_0.19|First public release version.|


## Copyright

Copyright FUJITSU LIMITED 2019


