# adder-verilog
module top_module (
    input [3:0] x,
    input [3:0] y, 
    output [4:0] sum);
    wire [4:0]w;
    assign w[0]=1'b0;
    genvar i;
    generate
        for(i=0;i<=3;i=i+1) begin : g_fa
            assign sum[i]=x[i]^y[i]^w[i];
    		assign w[i+1]=(x[i]&y[i])|(w[i]&(x[i]^y[i]));
        end
    endgenerate
    assign sum[4]=w[4];
endmodule
